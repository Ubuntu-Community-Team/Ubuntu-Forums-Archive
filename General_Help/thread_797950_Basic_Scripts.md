---
title: "Basic Scripts"
date: 2008-05-17
forum: General Help
---

### Post by Cilionelle on 2008-05-17
I would like to write a simple script allowing me to change the dir and then run a .jar file from the command line.  The scripting tutorial is a little over my head, and I was wondering if someone would mind giving me a hand.

The commands are simple:

```
cd /AoI/bin
java -jar AOILauncher.jar
```

How do I get this to run from the command line, with out always having to type it in.  It would also be awesome to know how to assign it an icon on the desktop and just double click it to run, but first things first, eh?

Cheers!

---

### Post by ibuclaw on 2008-05-17
1) This command should work like this:
```
java -jar /AoI/bin/AOILauncher.jar
```

2) To simplify it, we can create an alias in your .bashrc script.
```
gedit ~/.bashrc
```
And add to the bottom of the file:
[PHP]alias aoilaunch='java -jar /AoI/bin/AOILauncher.jar'[/PHP]
Save the file and restart the script by typing in this:
```
. ~/.bashrc
```
Now whenever you type in "**aoilaunch**" the program should run!

3) Right Click on the desktop, select "Create Launcher" and paste this into the "command" box:
```
java -jar /AoI/bin/AOILauncher.jar
```
Give it a name, and a desktop icon. And click "OK" to save it.

All the above ways should work just fine.
If they don't, say so and I'll corect myself.

Regards
Iain

---

### Post by Cilionelle on 2008-05-17
Thanks for the help, Iain.  I'm still having some troubles, tho, with both options.

1st, the launcher (that I made from the desktop) is not responding.  Double-clicking, etc, no avail.  I've checked the command and it is fine.

2nd, the aoilauncher alias isn't working either.  I'm getting an "Unable to access jarfile /AoI/bin/AOILauncher.jar" message.  I get the same message when I'm just running the .jar from the commandline, without changing the directory first.  Once I'm in the directory, everything works fine.

Again, thanks for your help.

Cheers!

---

### Post by ibuclaw on 2008-05-17
Where is the exact location of the folder AOI?

Is it in your home folder?

If so, change "/AOI/bin/" to "/home/**<username>**/AOI/bin".
Replace <username> with your actual username.

ie, for me:
```
/home/iain/AOI/bin/AOILauncher
```

Regards
Iain

---

### Post by Cilionelle on 2008-05-17
Again, thanks for your help.

Changing the path got a better response, but it wasn't a good one on the whole!  (I've called the alias 'aoi' for convenience' sake.)

The response was:

```
tom@miros:~$ aoi
java.io.FileNotFoundException: /home/tom/./UpdateConfiguration.xml (No such file or directory)
        at java.io.FileInputStream.open(Native Method)
        at java.io.FileInputStream.<init>(FileInputStream.java:106)
        at java.io.FileInputStream.<init>(FileInputStream.java:66)
        at sun.net.www.protocol.file.FileURLConnection.connect(FileURLConnection.java:70)
        at sun.net.www.protocol.file.FileURLConnection.getInputStream(FileURLConnection.java:161)
        at com.sun.org.apache.xerces.internal.impl.XMLEntityManager.setupCurrentEntity(XMLEntityManager.java:653)
        at com.sun.org.apache.xerces.internal.impl.XMLVersionDetector.determineDocVersion(XMLVersionDetector.java:186)
        at com.sun.org.apache.xerces.internal.parsers.XML11Configuration.parse(XML11Configuration.java:771)
        at com.sun.org.apache.xerces.internal.parsers.XML11Configuration.parse(XML11Configuration.java:737)
        at com.sun.org.apache.xerces.internal.parsers.XMLParser.parse(XMLParser.java:107)
        at com.sun.org.apache.xerces.internal.parsers.AbstractSAXParser.parse(AbstractSAXParser.java:1205)
        at com.sun.org.apache.xerces.internal.jaxp.SAXParserImpl$JAXPSAXParser.parse(SAXParserImpl.java:522)
        at org.jdom.input.SAXBuilder.build(SAXBuilder.java:453)
        at org.jdom.input.SAXBuilder.build(SAXBuilder.java:810)
        at org.jdom.input.SAXBuilder.build(SAXBuilder.java:789)
        at com.desertphoenix.risen.RisenLauncher.loadConfiguration(RisenLauncher.java:138)
        at com.desertphoenix.risen.RisenLauncher.<init>(RisenLauncher.java:37)
        at com.desertphoenix.risen.RisenLauncher.main(RisenLauncher.java:199)
java.lang.NullPointerException
        at java.io.File.<init>(File.java:222)
        at com.desertphoenix.risen.RisenLauncher.<init>(RisenLauncher.java:38)
        at com.desertphoenix.risen.RisenLauncher.main(RisenLauncher.java:199)
```

An error message is displayed by the .jar after this, saying that I need to e-mail the creator.  I've done that once before, and he said to make a script to handle the 'cd' and the 'java -jar...' bits.

NB: I don't get this error when running the file from the command line following a 'cd' to the AoI/bin directory.

---

### Post by ibuclaw on 2008-05-17
I suppose, but I can't see why a one liner wouldn't work if you typed it in properly (remember, my examples can only get you so far as I do not know how your filesystem is structured, it is you who must ensure that the script is pointing to the right location)...

[PHP]
alias aoi='cd /path/to/AOI/bin/
           java -jar AOILauncher.jar'
[/PHP]
Again, let me know how it goes.


Regards
Iain

---

### Post by Cilionelle on 2008-05-17
The path is correct, etc.  The 'aoi' alias now only does the 'cd' command! :D
Did I miss something in the middle of the alias creation?  Is it spaces or tabs to get them lined up?  Does it even matter?

---

### Post by Cilionelle on 2008-05-18
Bump.

---

### Post by ibuclaw on 2008-05-18
Sorry, (I fell asleep).

Erm, try adding a semicolon after the first line.
Though, it shouldn't make a difference...
Also, maybe brackets will solve this error?

Oh, and I use spaces, but as long as it start's with a **'** and ends with a **'** it should read it all in just fine.
[PHP]
alias aoi='{
    cd /path/to/AOI/bin/;
    java -jar AOILauncher.jar
}'
[/PHP]
I've managed to get all the above working with [this Java/Swing app.]("http://sourceforge.net/project/platformdownload.php?group_id=187032")

So I suppose any problems you having are really just beyond me, or have something to do with the startup script of the app you're running (as all my suggestions seem to work just fine).

[EDIT]
Just for testing sake, copy and paste this into your .bashrc file:
[PHP]
alias about='{                                                                                       
    LSB=$(lsb_release -d)                                                               
    echo                                                                                
    echo -n "Hello $USER,"                                                              
    echo " and Welcome to $(echo ${LSB/*:/})."                                          
    echo "I see that you are logged in using the $DESKTOP_SESSION desktop settings."    
    echo -n "I also see that you are currently using the $TERM console "                
    echo "with the ${SHELL#/*/} shell."                                       
    echo "Your home folder is $HOME, you are currently in the ${PWD#$HOME/} directory." 
    echo                                                                                
    echo $(fortune)                                                                     
    echo                                                                                
    echo "I am in your head..."                                                         
}'
[/PHP]
Close and Re-open your console, then type in "about".

Regards
Iain

---

### Post by radagast1155 on 2008-05-20
:popcorn: Thanks a bunch for the info on making the programs work w/o all the typing

---

