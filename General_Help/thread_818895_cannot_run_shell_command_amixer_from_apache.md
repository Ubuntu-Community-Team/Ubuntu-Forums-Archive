---
title: "cannot run shell command amixer from apache"
date: 2008-06-04
forum: General Help
---

### Post by stevodude on 2008-06-04
Hi guys/gals.

have a page index.html with the following:

```
<html><body><h1>listen to teh wireless!</h1>
<!--#echo var="DATE_LOCAL" -->
<a href="http://10.0.0.1/phpscripts/off.php">Radio off</a><br>
<a href="http://10.0.0.1/phpscripts/on.php">Radio on</a><br>
<br>
<a href="http://10.0.0.1/phpscripts/volmute.php">Vol Mute</a><br>
<a href="http://10.0.0.1/phpscripts/volunmute.php">Vol UnMute</a><br>
<a href="http://10.0.0.1/phpscripts/volup.php">Vol Up</a><br>
<a href="http://10.0.0.1/phpscripts/voldown.php">Vol Down</a><br>
<br>
<a href="http://10.0.0.1/phpscripts/chan1.php">97.9 Classic FM</a><br>
<a href="http://10.0.0.1/phpscripts/chan2.php">98.7 SeaFM</a><br>
<a href="http://10.0.0.1/phpscripts/chan3.php">99.5 TrippleJ</a><br>
<a href="http://10.0.0.1/phpscripts/chan4.php">100.3 HotFM</a><br>
<a href="http://10.0.0.1/phpscripts/chan5.php">101.1 ABC Local Radio</a><br>
<a href="http://10.0.0.1/phpscripts/chan6.php">101.9 4MK</a><br>
<a href="http://10.0.0.1/phpscripts/chan7.php">102.7 Radio National</a><br>
<a href="http://10.0.0.1/phpscripts/chan8.php">104.3 ABC NewsRadio</a><br>
<a href="http://10.0.0.1/phpscripts/chan9.php">105.9 MurriFM</a><br>
<a href="http://10.0.0.1/phpscripts/chan10.php">107.5 Comminuty Radio 4CRM</a><br>
<br>
</body></html>
```

example that works.

on.php
```
<?php
exec ('/home/clarksws/on.sh > /dev/null 2>&1 -q');
header( 'Location:http://10.0.0.1/index.html' );
?>
```

on.sh
```
#!/bin/bash
/usr/bin/fm on
```

example that does nothing.

volmute.php
```
<?php
shell_exec ('/home/clarksws/volmute.sh');
header( 'Location:http://10.0.0.1/index.html' );
?>
```

volmute.sh
```
#!/bin/bash
/usr/bin/amixer set Line mute
```

now I can run ./volmute.sh from command line and it mutes the radio, I also can run volmute.php from command line (with php-cli) and runs ok.
but from web page it does nothing.
I removed header to see if any output is produced, but gives a blank page.

(note: in order to get the command 'fm' to work I had to chmod 777 fm...

regards, stevec.

---

### Post by stevodude on 2008-06-04
I've removed the sh script and put the command directly into the php file like so:

```
<?php
exec ('/usr/bin/amixer -c 1 set Line mute');
header( 'Location:http://138.77.152.86/index.html' );
?>
```

now in apache2 error.log I get "Invalid card number."

so this tells me apache is running the php script, and that amixer executes, but apache cannot see the card in someway?...

---

### Post by stevodude on 2008-06-04
I've removed the sh script and put the command directly into the php file like so:

```
<?php
exec ('/usr/bin/amixer -c 1 set Line mute');
header( 'Location:http://138.77.152.86/index.html' );
?>
```

now in apache2 error.log I get "Invalid card number."

so this tells me apache is running the php script, and that amixer executes, but apache cannot see the card in someway?...

I changed the php script to aumix, and this tells me in apache error logs, that I cannot access the mixer device.

so it's a permissions issue with apache accessing audio hardware, but is OK with /dev/radio0 ...

---

### Post by stevodude on 2008-06-06
it's OK, I've sort of fixed it.

added www-data to audio group, chomd 755 to /dev/radio* /dev/audio* /dev/mixer* /dev/dsp*

OH, only problem is I have to chmod everytime I boot to be able to get apache web to be able to access these devices, anyway I can make that stick?

---

### Post by arbourp on 2009-01-24
I've been playing with this, to do some similar things.
Just add www-data to the audio group.

edit the file /etc/group
find the line that says:
audio: x:29:username

and append 
,www-data

voila...

---

