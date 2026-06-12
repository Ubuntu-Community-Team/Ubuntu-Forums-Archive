---
title: "All compressed files corrupt?"
date: 2012-12-20
forum: General Help
---

### Post by MocroNL on 2012-12-20
Hello ubuntu gurus.

Everytime I download a compressed file from ftp or from a website it is always corrupt. It does not matter if it is a 7zip,tar,tar.gz,zip and rar! They are all corrupt. Anyone knows a solution to this???

Thanks in advance.

---

### Post by Grenage on 2012-12-20
I'd consider running a memtest, first off.

---

### Post by lordievader on 2012-12-20
Can you give a bit more info.
What are you trying to download, how are you downloading it? And how are you extracting the compressed file?

---

### Post by sudodus on 2012-12-20
Is it possible that you run your ftp client in ***ascii*** mode (expecting that you receive text files, and treat end-of-line characters in a special way)?

Check and if necessary, set ***binary*** mode and try downloading again.

---

### Post by MocroNL on 2012-12-20
Thank you guys for the reply's.

@Grenage 
I will do this but later on. Because this server is already in 'production'.

@lordievader
Iam trying to download gpsmap1.7 plugin for cacti([http://spiffdev.com/downloads/gpsmaps-downloads](http://spiffdev.com/downloads/gpsmaps-downloads)) But this happens to all compressed files I download... Iam downloading it via wget or mget(ftp). I work via ssh with a windows laptop. 

When zipped I use: unzip file.zip -d destination_folder
Tar: tar -xvf file.tar
Rar: unrar x [filename.rar]
7zip:7z x file.7z

@sudodus
I will try this and report back.

---

### Post by sudodus on 2012-12-20
If you have that problem with wget, I don't think your problem is about ascii/binary setting, but something else.

What if you compare a file that is not compressed?
Try to download some file where there is a checksum attached (for example md5sum)! Will it match (or will the file be corrupted)?

If you find no other file, try with the ubuntu mini iso file

[[COLOR="Red"]http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/mini.iso[/COLOR]]("http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/mini.iso")

with the md5sum ```
e4d16caf537be112f3dc9ba94e158cf7
```

After downloading change directory to where you have the downloaded file and run the following command

```
md5sum mini.iso
``` You should get the md5sum listed above (as output from the command).

---

### Post by MocroNL on 2012-12-20
This is what I get.

root@TLS-AMS-MON-10:/opt# md5sum mini.iso
e4d16caf537be112f3dc9ba94e158cf7  mini.iso

---

### Post by sudodus on 2012-12-20
> **MocroNL said:**
> This is what I get.

root@TLS-AMS-MON-10:/opt# md5sum mini.iso
e4d16caf537be112f3dc9ba94e158cf7  mini.iso
which indicates a successful download :-)

Is there something wrong when you uncompress (open) your compressed files?

Try file-roller!

```
file-roller 'compressed file'
```

---

### Post by coldcritter64 on 2012-12-20
> **MocroNL said:**
> This is what I get.

root@TLS-AMS-MON-10:/opt# md5sum mini.iso
e4d16caf537be112f3dc9ba94e158cf7  mini.iso

According to that you have saved the mini.iso to /opt and are doing an md5sum as root ?

Normally a user saves downloads to their home folder not the system and md5sum does not need to be run as root either when the file is saved to /home/<user> (always safest to use minimum privileges necessary to do the job.)  File roller may have permissions problems reading the file saved in /opt when run from your user account.

Are you operating as root while doing the downloads as well ? (may not necessarily be pertinent, I'm curious after seeing the terminal output above.)

Edit: if you do test file-roller on any archives in /opt or any system folder for that matter, run it as root to avoid problems (**although ideally you really shouldn't work as root or in the root filesystem for your personal files/work**)

"gksu file-roller" without the quotes, in terminal will run it as root (see bolding above)

---

### Post by sudodus on 2012-12-20
> **coldcritter64 said:**
> According to that you have saved the mini.iso to /opt and are doing an md5sum as root ?

Normally a user saves downloads to their home folder not the system and md5sum does not need to be run as root either (always safest to use minimum privileges necessary to do the job.)  File roller may have permissions problems reading the file saved in /opt when run from your user account.

Are you operating as root while doing the downloads as well ? (may not necessarily be pertinent, I'm curious after seeing the terminal output above.)

Edit: if you do test file-roller on any archives in /opt or any system folder for that matter, run it as root to avoid problems (**although ideally you really shouldn't work as root or in the root filesystem for your personal files/work**)

"gksu file-roller" without the quotes, in terminal will run it as root (see bolding above)
+1

Good observation :-)

I agree: download files as normal user if possible, and save the file with normal permissions. At least newer Ubuntu desktop systems default to saving downloaded files to a directory under your home directory: 'Downloads'.

---

### Post by MocroNL on 2012-12-20
Iam using the account root because I need to install a plugin for cacti and it makes it easier with permissions (no sudo) I guess. And even if I use another user (non root) I still need to use the command sudo to get things done so it doesn't make any difference right?

I have tried to download(In home folder) as a normal user and still the download is "corrupted"... cannot extract the file.

I will do an gksu file-roller first checking what that exactly is:P

Greets

---

### Post by MocroNL on 2012-12-20
Output =

tls@TLS-AMS-MON-10:/downloads$ gksu file-roller
(gksu:4347): Gtk-WARNING **: cannot open display:

---

### Post by The Cog on 2012-12-20
What makes you think the download is corrupt? Can you post both the command you use and the error message it gives?

---

### Post by MocroNL on 2012-12-20
**This is when I download. Seems ok.**


tls@TLS-AMS-NS-03:~# wget [http://speedy.sh/65b6N/gpsmap1.7.zip](http://speedy.sh/65b6N/gpsmap1.7.zip)
--2012-12-20 16:24:30--  [http://speedy.sh/65b6N/gpsmap1.7.zip](http://speedy.sh/65b6N/gpsmap1.7.zip)
Resolving speedy.sh... 67.159.60.61, 67.159.60.74, 208.53.158.142, ...
Connecting to speedy.sh|67.159.60.61|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://speedyshare.com/65b6N/gpsmap1.7.zip](http://speedyshare.com/65b6N/gpsmap1.7.zip) [following]
--2012-12-20 16:24:30--  [http://speedyshare.com/65b6N/gpsmap1.7.zip](http://speedyshare.com/65b6N/gpsmap1.7.zip)
Resolving speedyshare.com... 67.159.60.66, 67.159.60.74, 208.53.158.142, ...
Reusing existing connection to speedy.sh:80.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.speedyshare.com/65b6N/gpsmap1.7.zip](http://www.speedyshare.com/65b6N/gpsmap1.7.zip) [following]
--2012-12-20 16:24:30--  [http://www.speedyshare.com/65b6N/gpsmap1.7.zip](http://www.speedyshare.com/65b6N/gpsmap1.7.zip)
Resolving [www.speedyshare.com](www.speedyshare.com)... 67.159.60.61, 67.159.60.66, 67.159.60.74, ...
Reusing existing connection to speedy.sh:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `gpsmap1.7.zip'

    [ <=>                                                                      ] 35,484       185K/s   in 0.2s

2012-12-20 16:24:30 (185 KB/s) - `gpsmap1.7.zip' saved [35484]



**This is when I try to unzip**

tls@TLS-AMS-NS-03:~# unzip gpsmap1.7.zip
Archive:  gpsmap1.7.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of gpsmap1.7.zip or
        gpsmap1.7.zip.zip, and cannot find gpsmap1.7.zip.ZIP, period.

---

### Post by sudodus on 2012-12-20
Is there any information about [FONT="Courier New"]gpsmap1.7.zip[/FONT] about the size or some checksum? Could there be other parts of a split file to download?

What's the result of
```
file-roller gpsmap1.7.zip
```
Will it complain in the same way or give some other clue about the problem?

And if still problems, please try to operate in an environment with full write access to the current directory!

---

### Post by oldos2er on 2012-12-20
It appears that the file gpsmap1.7.zip is actually a HTML document: ```
ann@ann-XPS-8100:~$ file gpsmap1.7.zip 
gpsmap1.7.zip: HTML document, ASCII text, with very long lines
```
It opened fine in a text editor.

---

### Post by coldcritter64 on 2012-12-20
> **MocroNL said:**
> **This is when I download. Seems ok.**


tls@TLS-AMS-NS-03:~# wget....Note the # symbol, downloading as root. You are instantly setting youself up for pemissions/ownership problems from the start. 

Please try to do this as normal user. Makes it easier for anyone to help you.

> **MocroNL said:**
> Iam using the account root because I need to install a plugin for cacti and it makes it easier with permissions (no sudo) I guess. And even if I use another user (non root) I still need to use the command sudo to get things done so it doesn't make any difference right?

I have tried to download(In home folder) as a normal user and still the download is "corrupted"... cannot extract the file.

I will do an gksu file-roller first checking what that exactly is:P

Greets
Intalling a plugin does NOT need the root account in use (normally disabled by default in Ubuntu). Doing so is unnecessarily risking your installation secutity wise and with regard to any errors you make (making an error as root can be VERY nasty for your install/data).

The preferred method here is to gain a root shell with,
```
sudo -i
``` this allows you to work as root while in you user account (installing the plugin), and you only need to enter your "sudo" password ONCE. Remember to close the root shell when complete.

You especially don't need to download the archive as root.

I have a feeling if you download normally and install from your account in the "preferred" manner (as is recommended on this site) you should have far less troubles, and even if you do have problems, helpers here will be "on the same page" as yourself.

---

### Post by MocroNL on 2012-12-21
@sudodus 
This is the output I get:
tls@TLS-AMS-MON-10:/downloads$ file-roller gpsmap1.7.zip

** (file-roller:28542): CRITICAL **: Failed to parse arguments: Cannot open display:

@oldos2er
I will change the file extension to html and put it in the cacti plugin map. Lets see if that works.

@coldcritter64
Thanks m8 for the tips. I have tried to do everything with a normal user but I got the same result...

---

### Post by sudodus on 2012-12-21
I think that oldos2er has found something interesting:

1. Could it be that you have downloaded the web page (html), where the zip file sits, instead of the zip file itself? Or can you use the file, when renamed so that the extension is html or htm?

2. What happens if you use a regular web browser, for example Firefox, to download your compressed files?

3. Try with more than one file, because that particular one might be stored with a bad extension (a mistake by the guy uploading it).

---

### Post by Wim Sturkenboom on 2012-12-21
[noparse]http://speedy.sh/65b6N/gpsmap1.7.zip[/noparse] is a webpage, not a zip file. Your wget result proves it. What made you think that it's a zip file?

:lolflag:

Navigate to that page and hover the mouse over the name gpsmap1.7.zip and you will see the real location of the actual file that you're interested in. You can also inspect the element or view the source of the page to find the location of the zip file.
The  actual zip is [http://www.speedyshare.com/65b6N/download/gpsmap1.7.zip](http://www.speedyshare.com/65b6N/download/gpsmap1.7.zip)

And if you try to access it directly (following the above link), you get redirected to the webpage. You can't download that file without going through their site.

speedyshare is clever :lolflag:

---

### Post by Wim Sturkenboom on 2012-12-21
You're file-roller error is probably because you don't have a graphical environment (server?).

---

### Post by MocroNL on 2012-12-21
@Wim Sturkenboom
Yes that is true. Sorry for not informing you that.

How can it not be a zip file?:P I understand when I inspect the element that it looks like a HTML page. But it is saved as a zip(by the creator of the plugin) for a reason I guess? And when I download it on my laptop(win7) it opens like a normal zip with different folders. And even if it was because I have to navigate through the speedy website. It still doesn't make sense, because I downloaded the file on my laptop(win7)and used it as an FTP server. So my Ubuntu could download it from there, but I still got the same result. I tried many ways to download it from different places.

@sudodus
1. I have downloaded the file on my laptop(win7)and used it as a FTP server, so my ubuntu server could download it from the FTP server. Tried that and had no succes...

2.I'am using the CLI but on my windows machine it downloads and opens without errors.

3.I get errors with every compressed file...

I hope this can be resolved...... 

I'am really thankfull to you guys for the support!

greets

---

### Post by Wim Sturkenboom on 2012-12-21
It's a webpage; therefore it's not a zip file. The full path might be something like [noparse]http://www.speedyshare.com/65b6N/gpsmap1.7.zip/index.html[/noparse]. The element that I'm talking about is not that page itself but the link gps1.7.zip that is at the top of the page.

Yoy can download that file, but only by going through that page and clicking the link. If you follow the link to the file directly (e.g. from my earlier post, you are redirected).

So how did you download that file in windows?

---

### Post by sudodus on 2012-12-21
> **MocroNL said:**
> @sudodus
1. I have downloaded the file on my laptop(win7)and used it as a FTP server, so my ubuntu server could download it from the FTP server. Tried that and had no succes...

2.I'am using the CLI but on my windows machine it downloads and opens without errors.

3.I get errors with every compressed file...

I hope this can be resolved...... 

I'am really thankfull to you guys for the support!

greets
I think it is easier to download files from the internet using GUI applications simply because many web pages are made for that. This is the case with this page as it is described by Wim Sturkenboom.

Sometimes it works directly to download via command line interfaces, e.g. wget, and that's fine.

But when you get problems, you might not see why unless you resort to a GUI web browser. In such cases, use a linux flavour with a graphic desktop interface or use Windows 7 in your laptop. Transfer the downloaded file via your local area network (if you want it in your server).

---

