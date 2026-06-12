---
title: "Nautilus Script - Mencoder automation"
date: 2008-03-28
forum: General Help
---

### Post by OrionFyre on 2008-03-28
Ok My canon point and shoot takes decent enough video shots. The only problem is it generates about 1.2 MB per second or more. So sending the family singing "happy birthday" to my aunt in China in a 150 MB file is unacceptable. Or even uploading video to the YouTube :)

So I have a little command line saved away in a text file I just paste into the command line and edit to fit my needs in terms of the filenames.
```
mencoder /media/CANON_DC/filename.avi -ovc h264 -oac mp3lame -lameopts abr:br=92 -o ~/Video/Incoming/filename-out.avi
```

I attempted rather vainly to create a nautilus script that would automate the process and allow me to process multiple files in one go.

Here is my attempt thus far:
```
#!/usr/bin/perl

###############################################################################
# Pass any video files selected to mencoder to encoding to specific format
# h264
###############################################################################

$script_title="Canon AVI --> H264 AVI";
$temp_file = "/tmp/avilog" . "-" . `date +'%s'`;

#Did that pesky user run the script sans file(s) selected?
if(!@ARGV)
{
	system("gdialog --title \"$SCRIPT_TITLE Error\" --msgbox \"Please select AVI files for this script. \" 400 400 2>&1");
	exit;
}


foreach $file (@ARGV)
{
	# grab the file type using 'file'
	$filetype=`file -i "$file"`; 

	# the 'file' output of a video stream will containg the string "video"
	if($filetype =~ /video/)
	{
		#It is a video format we will process it!
		#mencoder INPUT_FILE -ovc h264 -oac mp3lame -lameopts abr:br=92 -o ~/Video/OUTPUT_FILE
		system("echo \"'$file' - OK!\" 2>&1 >> $temp_file"); #ok
	}	
	else
	{
		# Apparently this is not an AVI ho-hum
		system("echo \"'$file' - Bad type: $filetype\" >> $temp_file"); #ok
	}
}

chomp($temp_file);
system("gdialog --title \"$script_title Results\" --textbox $temp_file 5 80 2>&1");

system("rm $temp_file");
```
So:
When I run the script on an AVI file a window pops up saying "OK!"
When I do the same on ohhh A JPG it says "Bad type:" ! 
When I run the script on a hundred files of varying types it says "OK!" on the video files and "BAD" on the non-video files.

So I am no ready to have it start throwing the files into mencoder.
The problem: This took me two+ hours to figure out. I took C+ in highschool (9 years ago) and my brain hurts now.

What I want to accomplish is to add in a little something indicating it is a converted file. Here is an example.
MVI_0160.AVI - Original filename
MVI_0160.h264.AVI
I want to add in the ".h264" And I know perl is awesome with string handling.. but ... *cries* my brain hurts.

what sort of code would I be looking to put in there to add this little string in the middle. I want to intelligently pull the extension off and not just assume it's only three characters. Sometimes you have '.mpeg'

---

