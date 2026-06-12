---
title: "Need to add new SED statement to remove a forward slash"
date: 2014-10-10
forum: General Help
---

### Post by bonelifer on 2014-10-10
Here's my current line:
```
BASENAME2=`echo "$2" | awk -F/ '{print $NF}' | sed 's/ /_/g' | sed 's/://g' | sed 's/?//g' | sed s/"'"/""/g`
```

I need to remove forward slashes from filenames as well but can't get it to work.

---

### Post by steeldriver on 2014-10-10
You can use a different character (instead of /) as the separator so that the / can be used as a normal character e.g.

```

$ echo 'some/file/name/' | sed 's|/||g'
somefilename
$ 
$ echo 'some/file/name/' | sed 's#/##g'
somefilename
$ 
$ echo 'some/file/name/' | sed 's@/@@g'
somefilename

```

---

### Post by Vaphell on 2014-10-10
> ```
BASENAME2=`echo "$2" | awk -F/ '{print $NF}' | sed 's/ /_/g' | sed 's/://g' | sed 's/?//g' | sed s/"'"/""/g`
```

why not bash builtins?
```
basename=${2##*/}  # strip path
basename=${basename//[:?\']} # remove :?'
basename=${basename// /_} # replace spaces with underscores
```

but where did you get forward slashes in filenames? They are illegal characters, you can't have them in file/dir names.

---

### Post by bonelifer on 2014-10-11
I'm using a mythtv userjob script. It gets the name from mythtv.  I need to remove any invalid characters. I then use it in the output name in handbrake. Right now I just change "/" to "-" via phpmyadmin before running a userjob. I'd like to fully automate this. I didn't use "bash builtins" because I based this on an existing script and I don't really know Bash and scripting, just able to Google Fu what I need into existence with enough searching. This however hasn't been one of the problems I've been able to fix. As soon as I've got a fix for this, I'll use the cleaned output, instead of the raw output in "$2".

```
#!/bin/bash

# First does a lossless MPEG-2(honorcutlist, -profile autodetct) transcode removing commericals(cutlist must be manually made before
# hand), then rebuilds the seek table. It uses handbrakecli to transcode the mpg to a mkv(H264, AAC). 
#
# Loosely based on mythtv-transcode-h264 version 0.8 by Defcronyke Webmaster.
#

# Arguments
# $1 must be the directory/file to be transcoded.
# $2 must be the output directory / file name. The directory must be writeable by the mythtv user
# $3 must be chanid
# $4 must be starttime
# the full userjob command in mythtv-setup should look like this:
#
# /usr/bin/mythtv-transcode-mkv.sh "%DIR%/%FILE%" "/media/Store/incoming/TV/%TITLE% - S%SEASON%E%EPISODE% - %SUBTITLE%.mkv" "%CHANID%" "%STARTTIMEUTC%"
#
# /usr/bin/mythtv-transcode-mkv.sh "%DIR%/%FILE%" "/media/Store/incoming/Movies/%TITLE%.mkv" "%CHANID%" "%STARTTIMEUTC%"
# 
#
# Create the temp directory used by this script:
# cd /var/tmp
# mkdir mythtv-tmp
#
# Set permissions on the temp directory used by this script:
# sudo chown -Rf mythtv:mythtv /var/tmp/mythtv-tmp/
# sudo chmod -Rf 0777 /var/tmp/mythtv-tmp/
#
# Make sure to set the MPEG autodetect-profile default to MPEG lossless in the backend.
# Create Transcoder profile named HDHR (or something else, remember to adjust
# the transcode line below the "Start transcoding to MPEG-4(XVID)" comment
#
#

# a temporary working directory (must be writable by mythtv user)
TEMPDIR="/var/tmp/mythtv-tmp"

# MythTV Install Prefix (make sure this matches with the directory where MythTV is installed)
INSTALLPREFIX="/usr/bin"

# don't change these
MYPID=$$
DIRNAME=`dirname "$1"`
DIRNAME2=`dirname "$2"`
BASENAME=`echo "$1" | awk -F/ '{print $NF}'`
BASENAME2=`echo "$2" | awk -F/ '{print $NF}' | sed 's/ /_/g' | sed 's/://g' | sed 's/?//g' | sed s/"'"/""/g`
BASENAME3=`echo "$2" | awk -F/ '{print $NF}' | sed s/.mkv//g`
CHAN="$3"
START="$4"
GROUP="Seen"

#Get mythtv database information
DBSERVER=""
DBUSER=""
DBNAME=""
DBPASS=""

#Try getting mythtv database information from existent files in the following order
MYTHDBFILE="/etc/mythtv/mysql.txt"
MYTHCONFIGFILE="/etc/mythtv/config.xml"
MYCONFIGFILE="~/.mythtv/config.xml"

if [ -f "$MYTHDBFILE" ]; then
	DBSERVER="$( grep "DBHostName=" $MYTHDBFILE | sed s/.*DBHostName=/\/ )"
	DBUSER="$( grep "DBUserName=" $MYTHDBFILE | sed s/.*DBUserName=/\/ )"
	DBNAME="$( grep "DBName=" $MYTHDBFILE | sed s/.*DBName=/\/ )"
	DBPASS="$( grep "DBPassword=" $MYTHDBFILE | sed s/.*DBPassword=/\/ )"
elif [ -f "$MYTHCONFIGFILE" ]; then
	DBSERVER="$( grep -E -m 1 -o "<DBHostName>(.*)</DBHostName>" $MYTHCONFIGFILE | sed -e 's,.*<DBHostName>\([^<]*\)</DBHostName>.*,\1,g' )"
	DBUSER="$( grep -E -m 1 -o "<DBUserName>(.*)</DBUserName>" $MYTHCONFIGFILE | sed -e 's,.*<DBUserName>\([^<]*\)</DBUserName>.*,\1,g' )"
	DBNAME="$( grep -E -m 1 -o "<DBName>(.*)</DBName>" $MYTHCONFIGFILE | sed -e 's,.*<DBName>\([^<]*\)</DBName>.*,\1,g' )"
	DBPASS="$( grep -E -m 1 -o "<DBPassword>(.*)</DBPassword>" $MYTHCONFIGFILE | sed -e 's,.*<DBPassword>\([^<]*\)</DBPassword>.*,\1,g' )"
elif [ -f "$MYCONFIGFILE" ]; then
	DBSERVER="$( grep -E -m 1 -o "<Host>(.*)</Host>" $MYCONFIGFILE | sed -e 's,.*<Host>\([^<]*\)</Host>.*,\1,g' )"
	DBUSER="$( grep -E -m 1 -o "<UserName>(.*)</UserName>" $MYCONFIGFILE | sed -e 's,.*<UserName>\([^<]*\)</UserName>.*,\1,g' )"
	DBNAME="$( grep -E -m 1 -o "<DatabaseName>(.*)</DatabaseName>" $MYCONFIGFILE | sed -e 's,.*<DatabaseName>\([^<]*\)</DatabaseName>.*,\1,g' )"
	DBPASS="$( grep -E -m 1 -o "<Password>(.*)</Password>" $MYCONFIGFILE | sed -e 's,.*<Password>\([^<]*\)</Password>.*,\1,g' )"
fi

fnMoveToWatchedGroup()
{
    #Move the recording to a group called Seen, so that they don't get prematurely deleted in the Deleted group.
	echo "UPDATE recorded SET recgroup="\"$GROUP\"" WHERE chanid="\"$CHAN\"" AND starttime="\"$START\""" > $TEMPDIR/mythtmp-$MYPID/watched.sql	
	mysql -h $DBSERVER -u $DBUSER -p$DBPASS $DBNAME < $TEMPDIR/mythtmp-$MYPID/watched.sql
}

fnUpdateStatus () # $1-message
{
    #Update jobqueue comment for mythweb.
	echo "UPDATE jobqueue SET comment="\"$1\"" WHERE chanid="\"$CHAN\"" AND starttime="\"$START\"" AND status="4"" > $TEMPDIR/mythtmp-$MYPID/upd.sql
	mysql -h $DBSERVER -u $DBUSER -p$DBPASS $DBNAME < $TEMPDIR/mythtmp-$MYPID/upd.sql
}

fnNotify_Growl()
{
    local host=192.168.1.141
    local port=23053
    if nc -w 5 -z ${host-ip} ${port} 2>/dev/null
    then
    python /usr/local/bin/send.py "$BASENAME3"
    fi
}

# play nice with other processes
renice 19 $MYPID
ionice -c 3 -p $MYPID

# make working dir, go inside
mkdir $TEMPDIR/mythtmp-$MYPID
cd $TEMPDIR/mythtmp-$MYPID

# remove commercials and rebuild index
# 
fnUpdateStatus "Cutting commercials"
$INSTALLPREFIX/mythtranscode --chanid "$3" --starttime "$4" --honorcutlist -p autodetect
fnUpdateStatus "Rebuilding index"
$INSTALLPREFIX/mythcommflag --file "$1" --rebuild

#Find the width of the current recording. Then decided whether or not it's HDTV.
fnUpdateStatus "Getting Width of $BASENAME3"
width=$(mediainfo --Inform="Video;%Width%" "$1".tmp)

if [ $width -ge 1280 ]
  then
fnUpdateStatus "Width of $BASENAME3 is 1280 or greater"
$INSTALLPREFIX/HandBrakeCLI -i "$1".tmp -o "$2"  --encoder x264 --quality 20.0 --rate 29.97 --pfr --aencoder faac --ab 160 --mixdown dpl2 --drc 1.0 --format mkv --decomb --subtitle scan --native-language English --native-dub --large-file --maxWidth 720 --loose-anamorphic --optimize --markers
  
  else
fnUpdateStatus "Width of $BASENAME3 is less than 1280" 
$INSTALLPREFIX/HandBrakeCLI -i "$1".tmp -o "$2"  --encoder x264 --quality 20.0 --rate 29.97 --pfr --aencoder faac --ab 160 --mixdown dpl2 --drc 1.0 --format mkv --decomb --subtitle scan --native-language English --native-dub --large-file --maxWidth 1920 --maxHeight 1080 --loose-anamorphic --optimize --markers
fi

fnMoveToWatchedGroup

# Copy new file to shows directory
#cp $DIRNAME/$BASENAME $DIRNAME2/$BASENAME2

# cleanup temp files
fnUpdateStatus "Cleaning up tmp files"
cd ..
rm -rf mythtmp-$MYPID

cd $DIRNAME
rm "$1".tmp

##fnUpdateStatus "$BASENAME3 has successfully completed transcoding"
sleep 10
fnNotify_Growl
```

---

### Post by Vaphell on 2014-10-11
fugly like hell, but if it works.... i am still curious what's up with these forward slashes. Like I said they are illegal in names (no wonder, it would be impossible to differentiate between file "a/b" and "file b in dir a", also written a/b?) so what's up with that?

btw, 
```
MYCONFIGFILE="~/.mythtv/config.xml"
...
elif [ -f "$MYCONFIGFILE" ];
```
this is not going to work
~ is a shorthand for user's home but it must not be inside quotes, otherwise shell doesn't "see" it and no tilde expansion occurs. Either drop "" in definition or use $HOME instead of ~ (preferably the latter, it always works)

---

### Post by bonelifer on 2014-10-11
In mythtv, they use names like these:
1022_20140529062600.mpg
1022 represents the channel, 20140529062600 is the concatenation of the date and time the recording started. 

Now lets say I've recorded CSI, season 11 episode 10
Show Name: CSI: Crime Scene Investigation
Subtitle: 418/427

The pretty name I'll end up with would be:
CSI: Crime Scene Investigation - [11x10] - 418/427

That would obviously not work so I need to remove it to get something like:
CSI Crime Scene Investigation - [11x10] - 418 427


Obviously I'd like it to have the show/movie names in my files I'm using in my XBMC library(ie I only use mythtv to record and then I use handbrake to shrink the files). Some movies or TV show subtitles(show description) may have "/". So I have to remove them or else it will do all that(it uses the cryptic name throughout it's internal stuff) and then it gets to the part where I do the handbrake portion(where it[bash script] will pass the pretty name to handbrake) and it will just crap out as if it had finished without error and I won't know till much later.

Also I haven't been able to incorporate any of that myself. Any help from someone who understands the situation I'm in would be appreciated.

As for the other part those are possible locations for files that contain the DB credentials for mythtv. I guess one of the others is correct in my situation and it just works, so I didn't notice.

---

