---
title: "winzip files"
date: 2008-01-03
forum: General Help
---

### Post by ladybluballs on 2008-01-03
hi I need to  install a utility that will open a winzip file I have unrar installed but it does not handle a winzip file,or not for me it will open it but you cant do anything with it I also need instructions on how to install any utility for this type file thanks

---

### Post by PeterJS on 2008-01-03
The ubuntu archive manager handles zip files out of the box, you should be able to just double click on the file to open it. On the command line the unzip program will unzip a zip file, I believe that unzip is installed by default, if not it's in the repositories.

---

### Post by Kzin on 2008-01-03
Or, if you are looking for a command line utility, unzip works too.

---

### Post by ladybluballs on 2008-01-03
> **PeterJS said:**
> The ubuntu archive manager handles zip files out of the box, you should be able to just double click on the file to open it. On the command line the unzip program will unzip a zip file, I believe that unzip is installed by default, if not it's in the repositories.

that does not seem to work it will take file out of zip package but its no good

---

### Post by PeterJS on 2008-01-03
Odd, try with the commandline unzip. Are you sure it's a good zip?

---

### Post by ladybluballs on 2008-01-03
> **PeterJS said:**
> Odd, try with the commandline unzip. Are you sure it's a good zip?

yes I think its good,I have even tried a different zip file same problem what all goes with this command you mentioned thanks

---

### Post by PeterJS on 2008-01-03
```

unzip *filename*

```

---

### Post by ladybluballs on 2008-01-03
> **PeterJS said:**
> ```

unzip *filename*

```

that command does not work either I entered the file name exastly as its named on my desktop and I get file not found

---

### Post by p_quarles on 2008-01-03
> **ladybluballs said:**
> that command does not work either I entered the file name exastly as its named on my desktop and I get file not found
Type:
```
cd ~/Desktop
```
and then try again.

---

### Post by ladybluballs on 2008-01-03
> **p_quarles said:**
> Type:
```
cd ~/Desktop
```
and then try again.

that does not work either says file not found

---

### Post by p_quarles on 2008-01-03
> **ladybluballs said:**
> that does not work either says file not found
Clearly the file is there somewhere, but you need to be in the right directory before the unzip command can find it. Do you have a folder set aside for downloads -- anything like that?

Essentially, if you can find the correct path to the file, you'll stop getting the "file not found" error.

---

### Post by rainwalker on 2008-01-03
In a terminal, do 
```
cd /path/to/file
```replacing that with the path to the file you want to unzip. Then do
```
unzip file
```replacing "file" with the name of the file.
If you want to be absolutely sure you're getting the file name right, you can type
```
ls
```which will list all of the files in whatever directory you're in, and you can copy/paste it (Control + Shift + C  to copy, Control + Shift + V to paste, or you can highlight the name and middle-click with your mouse to paste as well)

---

### Post by ladybluballs on 2008-01-03
> **rainwalker said:**
> In a terminal, do 
```
cd /path/to/file
```replacing that with the path to the file you want to unzip. Then do
```
unzip file
```replacing "file" with the name of the file.
If you want to be absolutely sure you're getting the file name right, you can type
```
ls
```which will list all of the files in whatever directory you're in, and you can copy/paste it (Control + Shift + C  to copy, Control + Shift + V to paste, or you can highlight the name and middle-click with your mouse to paste as well)

Archive:  UpgradeV106exe
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of UpgradeV106exe or
        UpgradeV106exe.zip, and cannot find UpgradeV106exe.ZIP, period.

[this is what I get]

---

### Post by rainwalker on 2008-01-03
> **ladybluballs said:**
> Archive:  UpgradeV106exe
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of UpgradeV106exe or
        UpgradeV106exe.zip, and cannot find UpgradeV106exe.ZIP, period.

[this is what I get]

Right-click on the file and go to "Properties"; what type of file does it say it is?

---

### Post by ladybluballs on 2008-01-03
> **rainwalker said:**
> Right-click on the file and go to "Properties"; what type of file does it say it is?

it says its a zip archive  its 192.6kb

---

### Post by rainwalker on 2008-01-03
Weird...
If you move it to your desktop, then right click on it and choose "Extract Here", what happens?

---

### Post by ladybluballs on 2008-01-03
> **rainwalker said:**
> Weird...
If you move it to your desktop, then right click on it and choose "Extract Here", what happens?

it places a unusable file on my desktop   [this download is a file transfer utility thats was designed for windows but people have had success running it with wine]

---

### Post by rainwalker on 2008-01-03
Hm...
Well, you could try going back to the place where you downloaded it and try again, but instead of saving it you could tell Firefox to open it with the archive manager instead (or file roller, whichever it says)

---

### Post by Kzin on 2008-01-03
Judging by the name its not a zip file but a self extracting zip file.  I haven't done it before, but it should be extractable...
What is the original link to the file and I'll see if I can get it to go.

---

### Post by dagnabit dang doohickey on 2008-01-03
UpgradeV1.06.exe *is* the extracted/unzipped file.

---

### Post by ryanVickers on 2008-01-03
anyone need the best RAR tool ever? SIGNATURE!!! :D:D:D

;)

---

### Post by Kzin on 2008-01-03
> **dagnabit dang doohickey said:**
> UpgradeV1.06.exe *is* the extracted/unzipped file.

If it is not a windows self extracting zip, then there isn't much I can do to help as I don't know much about WINE (Except how to drink it to excess) =)

---

### Post by dagnabit dang doohickey on 2008-01-03
What I'm saying is that ladybluballs got what she wanted: UpgradeV1.06.exe
UpgradeV1.06.exe is the binary that she extracted from the zip file.

Edit: There's also the possibilty that it was never zipped to begin with and she downloaded the binary itself.

---

### Post by ladybluballs on 2008-01-03
> **dagnabit dang doohickey said:**
> What I'm saying is that ladybluballs got what she wanted: UpgradeV1.06.exe
UpgradeV1.06.exe is the binary that she extracted from the zip file.

yes thats how it extracted but it was supposed extract as a utility tool for sending files or receiving files from computer to another device but instead of the tool it opened as a binary but in windows it will open as it was supposed to.my windows os went down again taking a expensive harddrive with it,thats the reason I want to make the transition to linux

---

### Post by p_quarles on 2008-01-03
> **ladybluballs said:**
> yes thats how it extracted but it was supposed extract as a utility tool for sending files or receiving files from computer to another device but instead of the tool it opened as a binary but in windows it will open as it was supposed to.my windows os went down again taking a expensive harddrive with it,thats the reason I want to make the transition to linux
It may work in Wine, but first you have to tell Wine to run it. It doesn't happen magically. Here's a basic guide:
[http://www.winehq.org/site/howto](http://www.winehq.org/site/howto)

EDIT: Also, a binary can be a tool. They are not mutually exclusive.

---

### Post by Kzin on 2008-01-03
> **ladybluballs said:**
> yes thats how it extracted but it was supposed extract as a utility tool for sending files or receiving files from computer to another device but instead of the tool it opened as a binary but in windows it will open as it was supposed to.my windows os went down again taking a expensive harddrive with it,thats the reason I want to make the transition to linux

I see, I was confused.  I don't really know how to set WINE up.

---

### Post by dagnabit dang doohickey on 2008-01-03
Aside from the fact that if you attempt this with Linux you will have to use wine, there is the issue of how well wine interfaces with serial ports. My usage of wine is intentionally limited to as little as possible, but if anybody else has knowledge/experience with wine and serial ports it would probably be information ladybluballs will need to know.

---

