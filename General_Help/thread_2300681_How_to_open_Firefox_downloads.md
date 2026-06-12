---
title: "How to open Firefox downloads?"
date: 2015-10-27
forum: General Help
---

### Post by mringer on 2015-10-27
L-Ub 14.04, Firefox 41.0.2,  upgrades installed as of today.

Firefox (version unknown) used to behave sensibly when I was running 12.04.

When I download a file using Firefox, I can usually open it in the same session. 
But there is no visible way to open a file that I downloaded on a previous occasion. 

Firefox menu bar > tools > downloads    produces a list of files headed "library".

When I double-click on a file, nothing happens
If I right click I get a small menu that  ** does not ** offer  "open"  or  "open with"
It offers:

Remove from history
open containing folder   (greyed out)
goto download page      (greyed out)
copy download link
clear downloads

Please is there any way to fix this?

I have no idea where this "library" is located, I cannot find in in my home
directory.

Also when I can open a file, Firefox often makes a bad choice of program. 
For example, it opens   .doc   files in Abiword and I want to use Libreoffice.

Thank you

---

### Post by buzzingrobot on 2015-10-27
Is Firefox actually putting files in $HOME/Downloads, or to another destination you may have told it to use? Is it set appropriately in "Preferences"?

Not sure Firefox will adhere to this, but right click on a file in the file manager and select "Properties" where you can usually set a default app to use to open files of that type.

---

### Post by ajgreeny on 2015-10-27
All of those things should be editable using FF preferences which may not be the same as your OS's default applications

You need to go to FF Edit->Preferences->Applications tab and set the correct application there. My FF toolbar shows a down-pointing arrow icon for displaying the progress of ongoing downloads, which also offers the library window you speak of, and I assume all the data that makes up that library window is in the hidden ~/.mozilla/firefox/*q2w3e4r5*.default/downloads.sqlite file (that is a random alphanumeric named sqlite file so will be different from the one I show).

---

### Post by buzzingrobot on 2015-10-27
My likely faulty memory is that previously when I clicked that down arrow and then clicked "Show All Downloads" that ~/Downloads opened.  Now, it's this "Library". Downloads in progress still seem to be in ~/Downloads; at least I couldn't find any evidence of a download-in-progress accumulating in ~/.mozilla. I will guess FF puts its data re: the download somewhere in there:  Cancelling a download in progress removes the partial file(s) from ~/Downloads but not the Library entry, and clicking that entry later can restart the download.

Like the OP, I did see some of the right-click options greyed out for reasons that weren't clear.

---

### Post by mringer on 2016-10-06
BUMP. 

I have now updated Firefox to 49.0 (latest) and the problems persist:

there is no known way to open a download from a previous session.

right-click a file: the item "open containing folder" is greyed out

Preferences: I set the download-to folder as   /home/Downloads
Firefox downloads somewhere else, I dont know where.

Please any advice?

---

### Post by howefield on 2016-10-06
> **mringer said:**
> ..there is no known way to open a download from a previous session.

Have you set the Privacy > History settings to clear "browsing and download history" on session close ?

---

### Post by yancek on 2016-10-06
> 
Preferences: I set the download-to folder as   /home/Downloads

Is that a typo?  There is no /home/Downloads directory, it should be /home/user/Downloads.  I don't have any problem accessing files using the method you describe as long as the file/directory is there.

---

### Post by mringer on 2016-10-07
Thank you who replied.

Howefield: Current setting is

Privacy > History > Firefox will > remember history

I have not knowingly changed this at any time


Yancek:  Yes this is a typo.  What displays is:

general > downloads > save file to >  v Downloads

where the    v    stands for a greenish downarrow. When I click on   Browse
it does indeed show the folder as      /home/username/Downloads
and this folder does exist.


Thank you both, Mark

---

### Post by howefield on 2016-10-08
If it isn't too onerous, you might try closing Firefox and renaming your ~/.mozilla folder which will force Firefox to create a fresh new default profile. If the behaviour is the same, you'll know it is by design.

---

### Post by mringer on 2016-10-10
> **howefield said:**
> If it isn't too onerous, you might try closing Firefox and renaming your ~/.mozilla folder which will force Firefox to create a fresh new default profile. If the behaviour is the same, you'll know it is by design.

Done that. The result is that FF continues to ignore the  

Preferences > downloads > save files to     which is still  /home/user/Downloads

it is actually saving to     /tmp/mozilla-(user)0

As before I can open the file immediately after I download it. If I shutdown & reboot, 
the file still appears in "show all downloads" but the folder in     /tmp   has
disappeared, which would seem to explain why I cant open the file. The folder

/home/user/Downloads

is owned by me with mode   700 .  So I did  (in   /home/user  )

chmod 777  Downloads

but FF continues to save into   /tmp/mozilla-(user)0

Please any ideas?

---

### Post by howefield on 2016-10-10
> **mringer said:**
> Done that. The result is that FF continues to ignore the ....

Then it sounds like something external to Firefox is the culprit, are you running an anti virus application, download manager, firewall or Firefox extensions ?

---

### Post by mringer on 2016-10-11
> **howefield said:**
> Then it sounds like something external to Firefox is the culprit, are you running an anti virus application, download manager, firewall or Firefox extensions ?

Thank you for your reply. I am not knowingly running any of these. How do I find out?

I have tried: searching with Synaptic's quick filter: here are search terms & I list what
packages were found that are installed

"firewall"   finds   ufw

"firefox"   finds firefox, xul-ext-ubufox, FF-locale-en, flash-plugin-installer,
gecko-media-player, pcmanfm

"virus"    finds nothing installed

"download"     finds  libquvi, libquvi-scripts, apt-transport-manager,
unattended-upgrades, transmission-gtk, auto-install-el, synaptic, 
gps-babel-gui, gps-babel-doc, ubuntu-dev-tools, ttf-mscorefonts-installer,
gps-babel, debootstrap, b43-fwcutter, firmware-b43-installer, dev-scripts,
texlive-utils, wget, openprinting-ppds

(sorry about the length) Only one I think might be relevant is   ufw ,
but 

ufw status verbose                   says

status: inactive

---

### Post by howefield on 2016-10-12
> **mringer said:**
> Thank you for your reply. I am not knowingly running any of these. How do I find out?....

Well, to be honest I'd expect that you would know what software you installed on top of what came by default, in other words if you do not know the answer, then the chances are that you haven't got anything conflicting with Firefox.

---

### Post by SeijiSensei on 2016-10-12
If you download an object that is opened by a helper application like a PDF document, Firefox writes the file to /tmp/mozilla-username0.  You can then save it from the menu inside the PDF reader.  If you download something with no helper application like an Ubuntu ISO image, it will write it to /home/username/Downloads.

---

