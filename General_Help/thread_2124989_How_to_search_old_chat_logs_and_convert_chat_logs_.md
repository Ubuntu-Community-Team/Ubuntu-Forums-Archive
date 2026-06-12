---
title: "How to search old chat logs and convert chat logs to a more readable format?"
date: 2013-03-12
forum: General Help
---

### Post by MarjaE on 2013-03-12
Hi,

I've been discussing story ideas with a friend of mine on Empathy and [since a partial upgrade last year disabled Empathy] on Pidgin. I can't search the old Empathy logs, for whatever reason, and can't reinstall Empathy because of dependencies issues. I want to find a practical way to convert these logs to another format which I can search and can more easily read.

I plan on switching to Mint eventually, but I am using Ubuntu 11.04 right now, if it matters. I know it's not supported, I have disabilities and I find a version of Gnome 2 the most accessible desktop given my disabilities, and I have read that some of the fixes I've made are no longer usable in more recent versions.

---

### Post by Vaphell on 2013-03-12
i don't use empathy so can you go to the empathy folder (probably ~/.empathy or ~/.config/Empathy or ~/.gconf/apps/empathy) and look in what format the archive is stored?

as for disabilities, care to list the tweaks you made that don't work in newer releases?
You can look into Mate, it's a forked gnome2 environment that is not abandoned like its predecessor. Afaik it can be easily installed via PPA.

---

### Post by MarjaE on 2013-03-12
Empathy uses .log format, Pidgin uses .html. For whatever reason, the desktop search won't touch either.

As far as the fixes go: I installed a patch to turn off touchpad tapping and gestures, and the patch works in Gnome 2 but didn't work in Xfce or KDE. I installed joystick software. I disabled the pop-up scrollbars, and this restored regular scrollbars. I widened the scrollbars. I don't recall exactly how I did all this. I understand that in the newer versions, disabling pop-up scrollbars no longer restores regular scrollbars.

---

### Post by Vaphell on 2013-03-12
but what the .log format means exactly? if i wanted to write a script i'd have to know how to parse it. If i had any .log file i'd look myself but i don't, so... :)
Is it something like *USER(TIME): message* ?

> I disabled the pop-up scrollbars, and this restored regular scrollbars. I widened the scrollbars. I don't recall exactly how I did all this. I understand that in the newer versions, disabling pop-up scrollbars no longer restores regular scrollbars. 

that's not true, you can still disable overlay scrollbars and get oldschool bars spanning whole width/height of the window.
[http://askubuntu.com/questions/34214/how-do-i-disable-overlay-scrollbars](http://askubuntu.com/questions/34214/how-do-i-disable-overlay-scrollbars)
i just tested it in vboxed 12.10 and i have 'normal' scrollbars right before my eyes. 
Btw, i'd imagine it's actually easier to work with huge buttons that show up right under the cursor and require less precision than with rather slim bars.

You should give latest releases a spin in virtualbox or on a separate test partition so you can stay in touch and test/break newer things without risking your tried and true setup, though i understand not everybody has time/patience to do that.

---

### Post by MarjaE on 2013-03-12
Well, I never had any luck with anything that's supposed to pop up when needed; these wouldn't pop up when I was trying to use them, and would pop up when I was trying to click on something else in the same area. I also tried Unity, but it didn't work for me. Newer versions might work better, but I understand it's designed around alt-tab to switch windows, and similar key combinations to search, and these are painful for me.

I don't know about vboxed, but I don't have the disk space on this partition for anything fancy.

I don't know how to answer your question about .log files. They open in the text editor/code editor.

<?xml version='1.0' encoding='utf-8'?>
<?xml-stylesheet type="text/xsl" href="log-store-xml.xsl"?>
<log>
<message time='20110611T11:55:33' id='*[id]*' name='*[name]*' token='*[string of characters]*' isuser='false' type='normal'>*[message]*</message>
</log>

---

### Post by Vaphell on 2013-03-13
so it's just a xml file. It would be trivial to whip up a script that would convert these logs to plaintext or something. Would the "TIME NAME: MSG" format be ok?
What is the exact location of these .log files and does their naming convention say something about the chronology?

---

### Post by zero2xiii on 2013-03-13
Hay,

Jumping the gun on the OP.

If he used pidgin to chat on the empathy network logs should be located:
~/.purple/logs/**Protocol**/**account_conversation_with**
eg:
~/.purple/logs/Empathy/Bob123/*

Also the files are usually named by date in format:
yyyy-mm-dd.hhmmss+gmt_offset.*
eg:
2011-01-05.221539+0200SAST.html
That means:
On 22:15:39 +02:00 GMT Chat was initialized on 2011-01-05


I have parsed most protocols on pidgin for study purposes of words most used etc. html2txt is my first choice.
 Pidgin can be configured to use xml/html or text formating for logs. xml/html being default (on my computer atleast).

An example tree will look like this:
~/.purple/logs/
```
.
&#9500;&#9472;&#9472; facebook
&#9474;   &#9492;&#9472;&#9472; user@yahoo.com
&#9474;       &#9492;&#9472;&#9472; 1417444932
&#9474;           &#9492;&#9472;&#9472; 2010-09-11.184410+0200SAST.html
&#9500;&#9472;&#9472; irc
&#9474;   &#9500;&#9472;&#9472; user@irc.freenode.net
&#9474;   &#9474;   &#9500;&#9472;&#9472; chanserv
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; 2012-09-16.170457+0200SAST.html
&#9474;   &#9474;   &#9492;&#9472;&#9472; #freedroid.chat
&#9474;   &#9474;       &#9492;&#9472;&#9472; 2012-09-16.170457+0200SAST.html
&#9474;   &#9492;&#9472;&#9472; user@irc.ubuntu.com
&#9474;       &#9500;&#9472;&#9472; #apt-get.chat
&#9474;       &#9474;   &#9492;&#9472;&#9472; 2011-03-29.190034+0200SAST.html
&#9474;       &#9500;&#9472;&#9472; #bash.chat
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-19.190444+0200SAST.html
&#9474;       &#9474;   &#9492;&#9472;&#9472; 2011-06-11.123456+0200SAST.html
&#9474;       &#9500;&#9472;&#9472; chanserv
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-11.112919+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-11.122720+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-19.184624+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-19.184759+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-19.190445+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-29.140157+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-29.155033+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-29.184053+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-29.200023+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-06-11.122704+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-06-11.123457+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-06-11.173500+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-07-02.205535+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-07-02.211222+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-07-03.154857+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-07-03.155228+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-07-18.175911+0200SAST.html
&#9474;       &#9474;   &#9492;&#9472;&#9472; 2011-12-07.103202+0200SAST.html
&#9474;       &#9500;&#9472;&#9472; #cubase6.chat
&#9474;       &#9474;   &#9492;&#9472;&#9472; 2012-02-19.121338+0200SAST.html
&#9474;       &#9500;&#9472;&#9472; #cubase.chat
&#9474;       &#9474;   &#9492;&#9472;&#9472; 2012-02-19.121350+0200SAST.html
&#9474;       &#9500;&#9472;&#9472; ##cubasedaw.chat
&#9474;       &#9474;   &#9492;&#9472;&#9472; 2012-02-19.121653+0200SAST.html
&#9474;       &#9500;&#9472;&#9472; #cubasedaw.chat
&#9474;       &#9474;   &#9492;&#9472;&#9472; 2012-02-19.121655+0200SAST.html
&#9474;       &#9500;&#9472;&#9472; floodbot1
&#9474;       &#9474;   &#9492;&#9472;&#9472; 2011-03-29.193455+0200SAST.html
&#9474;       &#9500;&#9472;&#9472; frigg
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-11.112904+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-11.192621+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-19.184612+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-19.184744+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-19.202154+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-29.140143+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-29.155024+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-29.184044+0200SAST.html
&#9474;       &#9474;   &#9492;&#9472;&#9472; 2011-03-29.195957+0200SAST.html
&#9474;       &#9500;&#9472;&#9472; #httpd.chat
&#9474;       &#9474;   &#9492;&#9472;&#9472; 2011-07-18.175441+0200SAST.html
&#9474;       &#9500;&#9472;&#9472; ioria
&#9474;       &#9474;   &#9492;&#9472;&#9472; 2011-03-29.200047+0200SAST.html
&#9474;       &#9500;&#9472;&#9472; #kdenlive.chat
&#9474;       &#9474;   &#9492;&#9472;&#9472; 2011-07-03.201216+0200SAST.html
&#9474;       &#9500;&#9472;&#9472; #nvidia.chat
&#9474;       &#9474;   &#9492;&#9472;&#9472; 2011-03-11.122428+0200SAST.html
&#9474;       &#9500;&#9472;&#9472; ##programming.chat
&#9474;       &#9474;   &#9492;&#9472;&#9472; 2011-03-19.190218+0200SAST.html
&#9474;       &#9500;&#9472;&#9472; #sdl.chat
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-07-02.211221+0200SAST.html
&#9474;       &#9474;   &#9492;&#9472;&#9472; 2011-07-03.155227+0200SAST.html
&#9474;       &#9500;&#9472;&#9472; ##sed.chat
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-06-11.123015+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-06-11.130423+0200SAST.html
&#9474;       &#9474;   &#9492;&#9472;&#9472; 2011-06-18.184012+0200SAST.html
&#9474;       &#9500;&#9472;&#9472; #ubuntu.chat
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-11.112917+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-11.122717+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-19.184622+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-19.184757+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-29.140153+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-29.155029+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-29.184051+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-03-29.200000+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-06-11.122703+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-07-02.205529+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2011-07-03.154854+0200SAST.html
&#9474;       &#9474;   &#9492;&#9472;&#9472; 2011-07-18.175910+0200SAST.html
&#9474;       &#9500;&#9472;&#9472; ##unavailable.chat
&#9474;       &#9474;   &#9492;&#9472;&#9472; 2011-06-11.173453+0200SAST.html
&#9474;       &#9492;&#9472;&#9472; #warzone2100-games.chat
&#9474;           &#9492;&#9472;&#9472; 2011-12-07.103201+0200SAST.html
&#9500;&#9472;&#9472; jabber
&#9474;   &#9492;&#9472;&#9472; user@gmail.com
&#9474;       &#9500;&#9472;&#9472; user@mxit.co.za
&#9474;       &#9474;   &#9492;&#9472;&#9472; 2010-07-05.214519+0200SAST.html
&#9474;       &#9500;&#9472;&#9472; user@gmail.com
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2012-11-13.212606+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2012-11-14.201124+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2012-11-16.201558+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2012-11-16.220343+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2012-11-17.202557+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2012-11-17.224315+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2012-11-18.192944+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2012-11-20.212047+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2012-11-26.175254+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2012-11-26.182303+0200SAST.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 2012-12-24.162313+0200SAST.html
&#9474;       &#9474;   &#9492;&#9472;&#9472; 2012-12-24.181217+0200SAST.html
&#9474;       &#9492;&#9472;&#9472; user@groupchat.google.com.chat
&#9474;           &#9492;&#9472;&#9472; 2011-10-20.215117+0200SAST.html
&#9492;&#9472;&#9472; tree

32 directories, 77 files
```

---

### Post by MarjaE on 2013-03-13
I have a backup folder full of the logs. It's just that they're a pain to read and impossible to search with the built-in desktop search. I don't have the processing power or spare disk space on this partition for special search software.

---

### Post by zero2xiii on 2013-03-13
Hay,

Have you tried opening it in a web browser?

Or simply try html2text on one file and see the result:
```
sudo apt-get install html2text
cat /path/to/file | html2text
```

if you like the result you can simply change all files in a directory to the alternative formating:
```
for file in ./*.log; do html2text "$file" > "$file.txt"; done
```

Note this might produce output with:
"That**&apos;**s" instead of "That**'**s"
"**&quot;**anything and everything**&quot;"** instead of "**"**anything and everything**"**"
etc.

But it is much more readable.

Cheers and good luck.
If this is not what you want, feel free to accept better advice from **Vaphell** as I am sure he has much more experience than me in scripting :)

---

### Post by Vaphell on 2013-03-14
quick and dirty scripting job that should convert all .log files to plain text in DAY HOUR NAME: MESSAGE format (files are created next to the .log files). In case you want some other format, point out which fields from that xml you want.
If you need something more specific eg clumping all files of a given contact into 1 big file or moving converted files somewhere i can upgrade it but i would need more info about the directory structure and naming conventions to figure out proper solution.

empathy_logs.sh:
```
#!/bin/bash

logpath=.     # put proper path here

while read -rd $'\0' f
do
  echo "converting $f"
  python empathy_logs.py "$f" > "$f.txt"
done < <( find "$logpath" -iname '*.log' -print0 )
```

empathy_logs.py:
```
#!/usr/bin/env python

import sys
from xml.etree.ElementTree import parse

xmldoc = parse( sys.argv[1] )
root = xmldoc.getroot()

for child in root:
  time = child.attrib["time"]
  time = time[0:4]+"-"+time[4:6]+"-"+time[6:8]+" "+time[9:17]
  name = child.attrib["name"]
  msg = child.text
  
  print "%s %s: %s" % ( time, name, msg )
```

bash script is just a wrapper around the python script


example with 2 dummy log files:
```
$ cat test*.log
<?xml version='1.0' encoding='utf-8'?>
<?xml-stylesheet type="text/xsl" href="log-store-xml.xsl"?>
<log>
<message time='20110611T11:55:33' id='[id]' name='[name1]' token='[string of characters]' isuser='false' type='normal'>some message</message>
<message time='20110611T11:55:36' id='[id]' name='[name4]' token='[string of characters]' isuser='false' type='normal'>some other message &amp;&lt;&apos;</message>
</log> 
<?xml version='1.0' encoding='utf-8'?>
<?xml-stylesheet type="text/xsl" href="log-store-xml.xsl"?>
<log>
<message time='20110611T11:55:33' id='[id]' name='[name1]' token='[string of characters]' isuser='false' type='normal'>abc</message>
<message time='20110611T11:55:34' id='[id]' name='[name2]' token='[string of characters]' isuser='false' type='normal'>def</message>
<message time='20110611T11:55:35' id='[id]' name='[name3]' token='[string of characters]' isuser='false' type='normal'>ghi</message>
<message time='20110611T11:55:36' id='[id]' name='[name4]' token='[string of characters]' isuser='false' type='normal'>jkl</message>
</log> 
$ ./empathy_logs.sh 
converting ./test1.log
converting ./test2.log
$ cat test*.log.txt
2011-06-11 11:55:33 [name1]: some message
2011-06-11 11:55:36 [name4]: some other message &<'
2011-06-11 11:55:33 [name1]: abc
2011-06-11 11:55:34 [name2]: def
2011-06-11 11:55:35 [name3]: ghi
2011-06-11 11:55:36 [name4]: jkl
```

---

### Post by MarjaE on 2013-03-16
Um... Sorry, I'm not even sure what bash and python are, except that python is a 'scripting language' which somehow differs from a programming language. I don't know what I'd enter the .sh and .py text in. I have something like 730 .log files to convert, too. Name formats are usually like 20110616.log with year, month, and day.

P.S. So bash is a shell, and I suppose the bash commands can be entered in the terminal? but python is different. and *Ubuntu for Non-Geeks *mentions it but doesn't explain it.

---

### Post by Vaphell on 2013-03-16
scripting languages are a subset of programming languages
Either way you create empty text files, paste the contents, type in the proper path in .sh file and run *bash whatever_name_you_picked.sh* in terminal. Bash part will call python part automatically (so you don't touch python at all) as long as the names of .py file and .py called in the bash script match.

If you want to have the logs conveniently glued into a single file for each friend account so the number is much lower (i would) tell me what is the exact structure, eg ~/.empathy_logs/protocol/user/20111121.log (i have no idea and i don't plan on using empathy to find out)



edit: assuming the files are located in dirs where last two parts are /your_acct/buddy_name (the internet and the poster above claim that) the script below should create a file named "buddy_name (your_acct).txt" in the configured destination dir for each dir that contains .log files.

empathy_logs2.sh
```
#!/bin/bash

shopt -s nullglob

# root dir of empathy logs
[COLOR="#0000FF"]logpath=.[/COLOR]
# destination dir for converted and merged files
[COLOR="#0000FF"]dest="$HOME/converted_logs"[/COLOR]

mkdir -p "$dest"

while read -rd $'\0' d
do
  files=( "$d"/*.log )
  (( "${#files[@]}"==0 )) && continue
  name=${d##*/}
  acct=${d%/*}; acct=${acct##*/}
  conv="$dest/${name} (${acct}).txt"
  rm "$conv" 2>/dev/null
  echo "converting log files from '$d' => '$conv'"
  for f in "${files[@]}"
  do
    python empathy_logs.py "$f" >> "$conv"
  done
done < <( find "$logpath" -mindepth 1 -type d -print0 )
```

same story: create empty file next to the .py file, name it whatever_you_want.sh
and then run
```
bash whatever_you_want.sh
```
you should get a dir full of txt files

---

### Post by MarjaE on 2013-03-19
Okay, I put one of the backup directories into the logpath= section of the bash script, but I'm getting an error saying there's "no such file or directory." I checked all my spelling capitalization, and backslashes, but maybe I'm missing something more basic.

---

### Post by Vaphell on 2013-03-19
are there empathy logs there?
logpath is where the source files are supposed to be located, dest where converted ones should land

when it says no file or directory, does it give a name?

---

### Post by MarjaE on 2013-05-13
Sorry for not getting back to you on this, didn't want to deal with fancy computer stuff with my rsi, but yes, there were/are empathy logs there.

---

