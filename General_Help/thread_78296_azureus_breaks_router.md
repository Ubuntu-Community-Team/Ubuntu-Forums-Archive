---
title: "azureus breaks router"
date: 2005-10-18
forum: General Help
---

### Post by jamesford on 2005-10-18
hello

since breezy my azureus keeps breaking my router (i dont know, crashes it i guess) - the only way to fix it is to restart the router manually.

very often the router dies just seconds after starting azureus, other times it can run for a few hours but performance gets gradually worse and eventually my network connection is brought to a halt

this never happened in hoary, so i suspect it may have something to do with the java package in breezy. IIRC azureus in hoary used suns java, but now something else is used.

anyone noticed something similar?

ive installed suns java manually but i think azureus keeps using the other java. how do i tell which one its using and how do i tell it to use sun java?

oh i should mention that using a different torrent client such as gnome-bittorrent or rufus  causes no problems whatsoever, however i find both these unsatisfactory so if someone could help me get azureus working properly again id be very happy

---

### Post by ember on 2005-10-18
I guess, it's a problem with the number of connection. My brother had similar problems with eMule and Windows. See, if you can limit the connections to a reasonable number and maybe it works then.

Best,
ember

---

### Post by jamesford on 2005-10-18
i thought of that and limited the number of connections several times to see if it got any better, in the end i was down to 10 connections and and the router still died so i dont think thats theproblem

---

### Post by ember on 2005-10-18
O.k. Then maybe the connections are not closed properly. Do you have the standard Java that comes with breezy installed? Or Suns JRE?

---

### Post by jamesford on 2005-10-18
ive got both. first i had the standard one and these problems happened. so i decided to install suns JRE, so now both are installed but i think azureus is using the standard one and not suns, but i dont know how to check what its using

---

### Post by ember on 2005-10-18
Try:

sudo ln -sf /usr/local/jre1.5.0_05/bin/java_vm /usr/bin/java_vm
sudo update-alternatives --install /usr/bin/java java /usr/local/jre1.5.0_05/bin/java 1

Or generally take a look at:
[http://www.ubuntuforums.org/showthread.php?t=76754&highlight=Sun+JRE](http://www.ubuntuforums.org/showthread.php?t=76754&highlight=Sun+JRE)

Best,
ember

---

### Post by FluffyElmo on 2005-10-18
I had a problem with Azureus not working with the new gcj Java. Just edit the azureus file and add the path to the correct (Sun) jvm where indicated. Works like a charm.

On my system:
```
nano azureus/azureus
```

---

### Post by jamesford on 2005-10-18
ember, that didnt seem to do anything :/

elmo, what file do u mean ? i dont seem to have a file called just azureus anywhere. ive looked at some other files but found none where i can set the path to the sun jvm...can you be more specific ?

thanks both

---

### Post by ember on 2005-10-18
Oh, I forgot ... afterwards do:

sudo update-alternatives --config java

And it may be that you have to correct the paths I gave you up there to match the ones on your system.

---

### Post by jamesford on 2005-10-18
ember, i suspect azureus is still using the other java package (but how can i tell for sure??) because its still suffering from the resize bugs that comes with the non-sun java package (at least sun java in hoary never caused the resize problem)

i think i need to tell azureus what java to use, but i dont know where to do it. fluffyelmo seems to have the right idea but im unsure what file hes refering to

---

### Post by ember on 2005-10-18
Hmm ... I guess, he's reffering to the azareus startup file - you could use the Sun JRE manually, by inserting something like:

/usr/local/jre1.5.0_05/bin/java azareus 

into the launcher.

What I was aiming at was to set the default java to Sun JRE.

---

### Post by jamesford on 2005-10-18
hmmm, the paths dont really match. but ive found it here and tried to run:

/usr/lib/j2re1.5-sun/bin/java azureus

does that look about right? i guess not cos i get this error msg:
Exception in thread "main" java.lang.NoClassDefFoundError: azureus

---

### Post by FluffyElmo on 2005-10-18
Yep, in whatever directory you unziped Azureus into there should be a shell script called 'azureus' that you run to start Azureus. If you open it there is a line rigth at the top where you can specify the JVM.

> #!/bin/bash

######## CONFIGURATION OPTIONS ########
JAVA_PROGRAM_DIR=""				# use full path to java bin dir, ex. "/usr/java/j2sdk1.4.2/bin/"
#PROGRAM_DIR="/home/username/apps/azureus"	# use full path to Azureus bin dir
#######################################


It is probably a good idea to set your default JVM to something more robust as well. But this should get you going...

---

### Post by jamesford on 2005-10-18
i dindt unzip azureus anywhere, i got a.deb file and dkpg'ed it. i cant find a file anywhere where i can specify these paths :/

---

### Post by jamesford on 2005-10-18
ah i think i got it now
elmo: i think i found your file in /usr/bin. it looks like:
#!/bin/sh
. /usr/share/java-config/libswt-3.1-java
if [ ! -d ~/.Azureus ]; then mkdir ~/.Azureus; fi
cd ~/.Azureus
exec java -Djava.library.path=/usr/lib \
	-classpath $JARS:Azureus2.jar:/usr/share/java/Azureus2.jar \
	org.gudy.azureus2.ui.swt.Main "$@"

is it that 2nd line i should edit ?
---------
ember:
launching /usr/lib/j2re1.5-sun/bin/java /usr/bin/azureus worked ONCE, now it doesent work again...how weird
edit: checking the bash history ir turns out i pasted the command on 2 lines so it didnt work after all :(

---

### Post by FluffyElmo on 2005-10-18
It might be simpler to uninstall the deb and just download the client from teh Azureus page. It's a pretty quick install. [http://azureus.sourceforge.net/howto_linux.php](http://azureus.sourceforge.net/howto_linux.php)

But looking at the script fragment you posted I think I would just hard-code the path the your jvm in the exec line:
```

Change:
exec java -Djava.library.path=/usr/lib \
To:
exec /usr/java/j2sdk1.4.2/bin/java -Djava.library.path=/usr/lib \

```
Or whatever the path to your JVM is. You may also have to change the java.library.path to say /usr/java/j2sdk1.4.2/jre/lib/ or just remove that part, leaving exec /usr/java/j2sdk1.4.2/bin/java \

But I think you have the right file. Back it up, experiment and Good Luck!

---

### Post by jamesford on 2005-10-18
i changed te exec line to this:
exec /usr/lib/j2re1.5-sun/bin/java -Djava.library.path=/usr/lib \

and azureus loads fine, but theres still the resize problem...so im still unsure

anyway, system monitor shows: [http://img305.imageshack.us/img305/9203/azu2py.jpg](http://img305.imageshack.us/img305/9203/azu2py.jpg)

does this look correct ? is it really using the sun java now ?

---

### Post by FluffyElmo on 2005-10-18
I'd try changing the lib directory as well. Right now I'd guess it's using the Sun JVM but the GCJ libraries. My guess would be:
exec /usr/java/j2sdk1.4.2/bin/java -Djava.library.path=/usr/java/j2sdk1.4.2/jre/lib/ \

But you may have to play around with other paths (/usr/java/j2sdk1.4.2/lib ?) or removing the library path altogether:
exec /usr/java/j2sdk1.4.2/bin/java \

---

### Post by jamesford on 2005-10-18
im getting a headache. removing the library path causes errors at launch and it all terminates. ive tried various other library paths that i thought might look correct but none work.

might as well uninstall the deb and do as u suggested some posts ago and download from the azureus site, but i gotta eat and some other stuff first. will post how it goes

thanks again for help

---

### Post by jamesford on 2005-10-18
hooray i got it working winth sun java and the resize bug is gone too! remains to be seen if this solves the router crashes but so far so good

thank you very much for your help

for the record heres what ive done
-uninstalled the  azureus.deb
-installed the sun java and followed instructions as described here [http://azureus.sourceforge.net/howto_linux.php](http://azureus.sourceforge.net/howto_linux.php)
-opened /home/username/programs/azureus/azures (thats where i chose to put azureus) and edited the JAVA_PROGRAM_DIR to look like JAVA_PROGRAM_DIR="/usr/lib/j2re1.5-sun/bin/"
-made a shortcut to /home/username/programs/azureus/azureus in the applications > internet menu

wohoo :D

---

