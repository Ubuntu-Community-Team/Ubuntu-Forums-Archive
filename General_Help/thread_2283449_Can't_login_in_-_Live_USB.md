---
title: "Can't login in - Live USB"
date: 2015-06-22
forum: General Help
---

### Post by pissedoffdude on 2015-06-22
I'm having trouble logging with the latest LIVE usb, 15 04 64-bit. When booting via USB, I'm presented with LIGHTdm window telling me to enter my username and password.  I have tried doing so, no luck  This is a live USB.  I've tried ubuntu/no pasword, ubuntu/password (and with capital 'U'), with nothing -- no difference.

I can't alt+fn it, because that simply presents me with a login window that I have no access to because my username/passwords are invalid.  Sound like the USB copy went wrong, or are we supposed to be presented with a login screen and be aware of the correct login credentials?

Thanks

---

### Post by yancek on 2015-06-22
As far as I know, there should be no need to login with a user name and/or password.  What software did you use to create the bootable usb?

---

### Post by nlee2 on 2015-06-22
root /no password = no go?

---

### Post by sudodus on 2015-06-22
There should be no password - you should get logged in directly into the live session.

Which flavour is it? Standard Ubuntu or ...?

Did you check the md5sum?

Which tool did you use to copy/flash/clone/install the iso file into the pendrive?

See this link, [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by RobGoss on 2015-06-22
There is no login when using a [COLOR=#000000]live session of any Ubuntu or other distributions as far as I know I'm not sure  why you are even getting a login request.[/COLOR]

---

### Post by ajgreeny on 2015-06-22
As others have said there should be no username and password when using a live system unless you logout and want to login again.  In that case the username is **ubuntu** and the password is left completely empty.

I think you probably have a corrupt image file (the iso file you downloaded) or a bad transfer to USB.

If the iso file does not match the md5sum which you can find at [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes") , download again, preferably using a torrent client, as that will check the file as it is downloaded.

---

### Post by ka55o5 on 2015-06-22
> **yancek said:**
> [..] software did you use to create the bootable usb?
I've found 15.04 Vivid to be quite temperamental, when creating a Live USB from Windows 7 x64 SP1; something that hadn't been present in many previous versions (not since while back, years!..:)). Finally, *Rufus* did it for me, FYI. :)

@```
https://rufus.akeo.ie/
```[color=gray]P.S. Running Xubuntu 15.04 Vivid Vervet +Core[/color]

---

### Post by pissedoffdude on 2015-06-22
Looks like Unetbootin doesn't believe in 15.04.  I've re-created it with dd and the issue has been resolved.  Thanks all.

---

