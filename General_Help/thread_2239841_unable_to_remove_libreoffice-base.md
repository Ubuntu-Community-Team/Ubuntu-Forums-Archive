---
title: "unable to remove libreoffice-base"
date: 2014-08-16
forum: General Help
---

### Post by bobmac on 2014-08-16
Folks,

Through  he Software Centre I tried to remove the LibreOffice-base product. The error messages I get are:

installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 768250 files and directories currently installed.)
Removing libreoffice-base ...
No diversion 'diversion of /usr/lib/libreoffice/share/basic/dialog.xlc to /usr/lib/libreoffice/share/basic/dialog.xlc.noaccess by libreoffice-base', none removed.
No diversion 'diversion of /usr/lib/libreoffice/share/basic/script.xlc to /usr/lib/libreoffice/share/basic/script.xlc.noaccess by libreoffice-base', none removed.
/var/lib/dpkg/info/libreoffice-base.postrm: 31: /var/lib/dpkg/info/libreoffice-base.postrm: Syntax error: end of file unexpected (expecting "fi")
dpkg: error processing libreoffice-base (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 libreoffice-base
Error in function: 

Is there any way that I can remove this product. I'm running v12.04LTS with all the latest updates.

Regards,

Bob

---

### Post by speartip on 2014-08-16
If removing libreoffice-base, I assume you want rid of libreoffice altogether off your system?
If so try running:
```
sudo apt-get remove --purge libreoffice*
```
from a terminal.
That always worked for me.

---

### Post by em3raldxiii on 2014-08-16
First off, why do you want to remove libreoffice?  It's not particularly huge, and it doesn't really hurt anything to have installed.  You can still install another office suite without having to remove LibreOffice.

Anyhoo ... if you're hell-bent on yanking it, I am not sure if this is the "correct" thing to do, but here's what I would do:

Open a terminal and run these:

**sudo apt-get update** This will update your software sources.
**sudo apt-get install -f   **This will attempt to repair broken packages.
**sudo apt-get remove --purge libreoffice* **This will remove libreoffice and purge the install information

You should not have to specify libreoffice-base.

There is a possibility that removing LibreOffice could make something else a little unstable.  Someone else will have to clarify that part.

---

### Post by em3raldxiii on 2014-08-16
Note that the *install -f* command may reinstall part of the LibreOffice that you've already removed.  That's okay, though ... starting from an unbroken package is a better plan.

---

### Post by vasa1 on 2014-08-16
OP specifically wants to remove one component of the LibreOffice suite, **Base**. I don't know if that's possible. If you totally uninstall LibreOffice, you can then choose to install only the component you want (plus whatever dependencies that requires).

For example, this is what I have:```
[03:34 PM] ~ $ dpkg --get-selections | grep libreoffice
libreoffice-base-core	
libreoffice-calc		
libreoffice-common		
libreoffice-core		
libreoffice-gtk			
libreoffice-help-en-us	
libreoffice-style-galaxy
libreoffice-style-human	
libreoffice-writer		
[03:34 PM] ~ $ 
```

---

### Post by nadrach on 2014-08-16
I hit an upgrade error from the first version of LO 4.3 to 4.3.0.4 where two incoming packages wanted to overwrite the same file and the upgrade to libreoffice-base failed. When I tried to remove LO completely, the not-upgraded libreoffice-base failed to remove. There was a line missing in the file **/var/lib/dpkg/info/libreoffice-base.postrm**.

It should read:

> #!/bin/sh

set -e


if [ "$1" = remove -o "$1" = abort-install -o "$1" = disappear ]; then
dpkg-divert --package $DPKG_MAINTSCRIPT_PACKAGE --remove --rename \
--divert /usr/lib/libreoffice/share/basic/dialog.xlc.noaccess \
/usr/lib/libreoffice/share/basic/dialog.xlc
dpkg-divert --package $DPKG_MAINTSCRIPT_PACKAGE --remove --rename \
--divert /usr/lib/libreoffice/share/basic/script.xlc.noaccess \
/usr/lib/libreoffice/share/basic/script.xlc
fi
if [ "$1" = abort-upgrade ] && dpkg --compare-versions "$2" lt dpkg --compare-versions "$2" lt 1:4.3.0~beta1-1; then
dpkg-divert --package $DPKG_MAINTSCRIPT_PACKAGE --remove --rename \
--divert /usr/lib/libreoffice/share/basic/dialog.xlc.noaccess \
/usr/lib/libreoffice/share/basic/dialog.xlc
dpkg-divert --package $DPKG_MAINTSCRIPT_PACKAGE --remove --rename \
--divert /usr/lib/libreoffice/share/basic/script.xlc.noaccess \
**/usr/lib/libreoffice/share/basic/script.xlc**
fi

# Automatically added by dh_installmenu
if [ -x "`which update-menus 2>/dev/null`" ]; then update-menus ; fi
# End automatically added section


exit 0 


but the line in **bold** was missing.

I used **sudo vi /var/lib/dpkg/info/libreoffice-base.postrm** in a terminal to edit the file and add the line. Then re-ran the remove OK.
I have now re-installed LO 4.3.0.4 clean.
The file is fixed in LO 4.3.0.4.

---

### Post by em3raldxiii on 2014-08-16
Aha, okay, that makes more sense.  I wasn't exactly sure what you were up to to start with.  I'm glad you have it all figured out.  If you haven't already, you should mark this thread as SOLVED via the thread tools link near the top of the page.

---

### Post by vasa1 on 2014-08-16
> **em3raldxiii said:**
> Aha, okay, that makes more sense.  I wasn't exactly sure what you were up to to start with.  I'm glad you have it all figured out.  If you haven't already, you should mark this thread as SOLVED via the thread tools link near the top of the page.
Only the OP can mark a thread [SOLVED]. 
The post above yours relates to fixing a failure to upgrade. OP's post relates to removing a component of LibreOffice.

---

### Post by em3raldxiii on 2014-08-17
@Vasa1 Uh, my bad ... for some reason I thought the above was a response by the OP ... sometimes I am not the brightest crayon in the box o.O

---

### Post by RandyNose on 2014-08-17
@[nadrach]("http://ubuntuforums.org/member.php?u=464730") [COLOR=#000000] [/COLOR]Thank you. 
This is exactly what I was looking for. ;)

This issue could come up for many people as it's affects an LTS version of Ubuntu and  Mint 13.

---

### Post by TedinOz on 2014-08-17
> **nadrach said:**
> I hit an upgrade error from the first version of LO 4.3 to 4.3.0.4 where two incoming packages wanted to overwrite the same file and the upgrade to libreoffice-base failed. When I tried to remove LO completely, the not-upgraded libreoffice-base failed to remove. There was a line missing in the file **/var/lib/dpkg/info/libreoffice-base.postrm**.

It should read:



but the line in **bold** was missing.

I used **sudo vi /var/lib/dpkg/info/libreoffice-base.postrm** in a terminal to edit the file and add the line. Then re-ran the remove OK.
I have now re-installed LO 4.3.0.4 clean.
The file is fixed in LO 4.3.0.4.

Hi...somewhat of a novice at all this. I was able to open **/var/lib/dpkg/info/libreoffice-base.postrm**. in the terminal as you described but unsure how to make the edit. Whilst I could move the cursor around within the terminal file, whenever I attempted to add the missing line, it came up as a new line at the bottom and not in the position nominated by you. 
You help will be appreciated. Thx

---

### Post by kostkon on 2014-08-18
> **TedinOz said:**
> Hi...somewhat of a novice at all this. I was able to open **/var/lib/dpkg/info/libreoffice-base.postrm**. in the terminal as you described but unsure how to make the edit. Whilst I could move the cursor around within the terminal file, whenever I attempted to add the missing line, it came up as a new line at the bottom and not in the position nominated by you. 
You help will be appreciated. Thx
Try with gedit
```
gksudo gedit /var/lib/dpkg/info/libreoffice-base.postrm
```

---

### Post by RandyNose on 2014-08-18
> **TedinOz said:**
> Hi...somewhat of a novice at all this. I was able to open **/var/lib/dpkg/info/libreoffice-base.postrm**. in the terminal as you described but unsure how to make the edit. Whilst I could move the cursor around within the terminal file, whenever I attempted to add the missing line, it came up as a new line at the bottom and not in the position nominated by you. 
You help will be appreciated. Thx

The example used VI, it's a simple text editor that works in non graphical environments. I used gedit myself, but any text editor should do. gedit, leafpad, kate, geany etc.

```

sudo gedit /var/lib/dpkg/info/libreoffice-base.postrm

```

Give that a try using the text editor that you've got on your system. 
Randy

---

### Post by kostkon on 2014-08-18
If 
```
sudo apt-get purge libreoffice-base
```
still doesn't work for you, try removing these 3 packages and then reinstall them
```
sudo apt-get purge libreoffice-base libreoffice-report-builder-bin libreoffice
sudo apt-get install libreoffice-base libreoffice-report-builder-bin libreoffice
```

---

### Post by TedinOz on 2014-08-18
@ kostkon and RandyNose...

Many thanks for your input and help. Gedit worked fine and was able to remove LO Base and update Manager is working fine again. My remaining question now is, which version of LO do I now install? My repository version shows as v 4.3.0-3, consistent with the update that caused all this. I note that nadrach said that he installed [COLOR=#000000] LO 4.3.0.4 clean where the file has been corrected. Do I proceed with re-installing the repository version through the terminal as suggested by kostkon above, or do I find and install [/COLOR][COLOR=#000000] LO 4.3.0.4 ? And if the latter, could you point me to where I find this?
I apologise for my caution but just taking baby steps here and your advice will be appreciated greatly.
Regards...Ted.[/COLOR]

---

### Post by QIII on 2014-08-18
After several hijackings, this has gone away from bobmac's original question/solution.

Please do not hijack the threads of others.  You see here what confusion that can cause.  Please start your own threads if you need help, or subscribe to the thread and politely watch for a resolution to your problem if it arises.

bobmac, you have the floor.

It would be appreciated if everyone would allow bobmac to get coherent help without the interference.

---

