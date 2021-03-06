genericfileage
--------------------------------------------------------------------------------

Counts time, in seconds, the last update in a file
position  to  tell  from  where  it  stopped.  Great   for  creating  monitoring
processes in real time logs that are being increased.

Changelog
--------------------------------------------------------------------------------

2015-02-06 - v1   - First Stable Release

Dependencies
--------------------------------------------------------------------------------

As a Perl script you will need to install via CPAN the Modules below:

	JSON
	File::stat
	Getopt::Std
	XML::Simple
	Config::Simple

How to Use
--------------------------------------------------------------------------------

CONF FILE:

Just  fill  the  configuration  file  with  the  values  for  key,  log, dbfile,
occurrence and outputformat, then run the script.

Legend:

	key: the indentificator that will be used by you to show in your monitoring
	interface.
	log: Log file that will be read by the script.
	dbfile: Position control file  used by the script to know the position for
	the next search execution.
	occurrence: The string that the script will look for. Also work with regex
	outputformat: xml, json or simple "key: value". You choise.

Example:

	key=""
	log="/var/log/messages"
	dbfile="genericseek.db"
	occurrence="error"
	outputformat="xml"

NOTE:

If your config file is empty for some reason, just run the script with -r option

DB FILE:

For  the  very  first time running the script this file must be created, so just
execute a "touch command" and leave it empty, the script will do the rest.

	# touch genericseek.db

Output Format
--------------------------------------------------------------------------------

This  is how the output will look depending of your choise (this is just a dummy
example OK?).

XML Output:

	<?xml version="1.0" encoding="UTF-8"?>
	<filematch>
		<timestamp>1234567890</timestamp>
		<key>bla</key>
		<value>50</value>
	</filematch>

JSON:

	{ "filemath": [
	        {"timestamp": 1234567890},
	        {"key": "bla"},
	        {"value": 50}
	]}

"key value":

	bla: 50 (no timestamp in here)
