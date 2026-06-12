---
title: "Azureus starts only from the console"
date: 2005-03-31
forum: General Help
---

### Post by Kiyone on 2005-03-31
I've installed Azureus on my Hoary, everything works fine when i start it from the console:
$ \opt\azureus\azureus

Now i want to make a menu entry with Menu Editor in Internet. I've made an entry for Azureus in Internet and in the command field i entered:
\opt\azureus\azureus

When i select the new entry, nothing happens, no error message. Same thing happens when i open a torrent link in Firefox and choose the location of azureus to open it with this application.

I've also checked "Run in Terminal", all i see when selecting the menu entry is a terminal windows for about a second or so.

Any ideas what i'm doing wrong?

*edit* just seen that i posted in the warty board, it's not my day :(

---

### Post by bored2k on 2005-03-31
I moved it to Hoary board if you don't mind ;)

Here is how you do it :
1. Open gedit [Applications>Accesories>Text Editor]
2. Type this in:
> 
#!/bin/sh
cd /opt/azureus; sh azureus

3. Save to azu.sh
4. Then
> chmod 755 azu.sh
5. Make the launcher with azu.sh ;)

---

### Post by Kiyone on 2005-03-31
Thanks for your fast reply.

Your solution also didn't work for me but the terminal window opened a bit longer so i had a chance to read the error message in the terminal. It was something like: "java exec not found", i created a link in usr/bin to the java executable and everything works smooth now.

I have no idea why it worked directly in the terminal, there should've been the same problem with the missing executable?!

BTW is it normal that the Java process ist still running after Azureus is closed, it wastes ~350mb of precious memory?

---

### Post by bored2k on 2005-03-31
I think your java is not properly configured. I suggest you create your own package like this:

1. Have universe, multiverse on [repositories]
> $ sudo apt-get update
$ sudo apt-get install build-essential
$ sudo apt-get install java-package java-common fakeroot

2. Get JRE 5.0 Update 2
[http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp)
Linux self-extracting file  (jre-1_5_0_02-linux-i586.bin, 15.78 MB) <- Or equivalent

3. fakeroot make-jpkg jre-1_5_0_02-linux-i586.bin

4. sudo dpkg -i sun-[whatever the name of the created file]

5. sudo apt-get install   sun-j2re1.5debian [if not available, sun-j2re1.5]

6. sudo update-alternatives --config java

7. sudo apt-get -f install

It works on mine like that .

[ [http://www.ubuntulinux.org/wiki/Java](http://www.ubuntulinux.org/wiki/Java) ]

---

