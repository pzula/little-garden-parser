## The Little Garden Parser

Working with my yearly garden plan CSV and converting it to Google Calendar events,
below are the patterns at play for the parser to be built:

- If the next line being parsed does not contain Date, Alt Date, and/or Crop, use the data from the previous line in those fields
- If above is true for more than one line, continue backward until Date, Alt Date, and/or Crop is found and use that data.
- Sometimes a date is shared amongst multiple crops. This backward-crawl needs to account for that. (i.e. 4/12-4/13, 5/8-5/9)
- If the Garden Action is 'Start', there will be no location. (Defaults to indoor greenhouses)
- If the Garden Action is 'Start', use the number from the '# Starts' row
- If the Garden Action is 'Transplant' or 'Direct Seed', use the number from the '# Plants' row, when available
- If the Variety name is empty, it is likely a Transplant of something that was previously Started; ignore Variety names here.
