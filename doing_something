#!/usr/bin/env python

from datetime import timedelta, datetime
import argparse

# Set runtime variables

# Parse the CLI arguments
argparser = argparse.ArgumentParser(
    description="Please enter values"
)

argparser.add_argument("-w", "--weeks", type=int,
                       help="number of weeks", default=0)
argparser.add_argument("-d", "--days", type=int, help="number of days", default=0)
argparser.add_argument("-H", "--hours", type=int,
                       help="number of hours", default=0)
argparser.add_argument("-m", "--minutes", type=int,
                       help="number of minutes", default=0)
argparser.add_argument("-s", "--seconds", type=int,
                       help="number of seconds", default=0)
argparser.add_argument("-i", "--input-format", type=str,
                       help="date input format string", default=default_format)
argparser.add_argument("-o", "--output-format", type=str,
                       help="date output format string", default=default_format)
argparser.add_argument("-u", "--utc", help="set to use UTC; otherwise, use local timezone", action="store_true")
argparser.add_argument(
    "date", type=str, help="date /time from which to calculate (defaults to current date / time)", default="", nargs="?")

args = argparser.parse_args()


# Calculate the starting date

# if we get nothing (or "now") then assume the current date / time
if ((args.date == None) or (args.date == "") or (args.date == "now")):
  if (args.utc):
    target_date = datetime.utcnow()
  else:
    target_date = datetime.now()

# if we get a string, attempt to parse that string into a datetime object
else:
    target_date = datetime.strptime(args.date, args.input_format)

# timedelta accepts relative values and returns a datetime object based on the
# relative value and the initial date
date_delta = timedelta(weeks=args.weeks, days=args.days,
                       hours=args.hours, minutes=args.minutes, seconds=args.seconds)

# perform the calculation
calculated_date = target_date + date_delta

# write the output to STDOUT in the requested format
print calculated_date.strftime(args.output_format)
