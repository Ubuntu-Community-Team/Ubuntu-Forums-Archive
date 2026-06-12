---
title: "Persistent, secure Ubuntu on USB drive"
date: 2013-01-08
forum: General Help
---

### Post by alnilamski on 2013-01-08
Okay, I searched all over and found some of my own answers to this, but I still need a little help.

I want to run Ubuntu from a USB drive in a persistent way. So e.g. if I save a file to Home, install an application, or tell Firefox to "Remember me" on Gmail, it stays there between boots. I've seen it done before, and I've used Tails, so I know it must be possible. So my first question is about how to set this up.

The answer I've found for myself so far is: use PenDriveLinux's _[Universal USB installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")_, along with an ubuntu ISO (downloading now). FYI I'm doing this from windows 7.
**Is this right? Or can the Ubuntu install disc make a persistent USB drive on its own?**
In that PenDriveLinux universal USB installer, **what does "_[Set up a persistent file size for storing changes]("http://www.pendrivelinux.com/wp-content/uploads/Universal-USB-Installer.png")_" mean? Will this set up an entirely separate, persistent partition, or does it just mean the home drive will be persistent?** All I want is for my programs, settings, and Home drive to persist.

My second question is about security. If I lose this stick, I mainly don't want someone to access my stored browser settings, e.g. the cookie that keeps me logged into gmail.
**I know Ubuntu natively supports an encrypted Home and Swap directory now. Is this sufficient to protect my browser settings?**

Also, crazy question, but I know Tails wipes the host computer's RAM when you log off. Is it really possible for someone to log onto the same host PC and access my data from the RAM? My guess is "it's extremely unlikely" but I'm curious to know.

---

### Post by Cheesemill on 2013-01-08
If you're worried about losing the USB drive then my suggestion would be to do a full installation on it using full drive encryption. This is exactly the same as a normal installation on a hard disk.

When you use either the 'Universal USB Installer' or the 'Startup Disc Creator' you are basically creating a Live CD, with the extra option of storing all of your saved data and installed programs in a separate file on the USB drive. This casper-rw file isn't encrypted so anyone who has hold of the device could access all of your files.

By doing a full installation instead you can choose to have everything encrypted.

For the pros and cons of each method take a look at this post...
[http://ubuntuforums.org/showpost.php?p=10293555&postcount=2](http://ubuntuforums.org/showpost.php?p=10293555&postcount=2)

Also take a look through oldfred's posts on installing to a USB stick...
[http://ubuntuforums.org/showpost.php?p=12337697&postcount=2](http://ubuntuforums.org/showpost.php?p=12337697&postcount=2)

---

### Post by alnilamski on 2013-01-08
Thanks, that helps! So it looks like I want a full install. Encrypting the entire OS might be overkill, but we'll see.

The big remaining questions are:
[LIST=1]
[*]Is the browser data (cookies etc.) located entirely within the home directory? **Will selecting "encrypt home directory" be enough to secure the browser data?** This is really my main objective here, is preventing someone who finds the stick from, say, logging into my cookied email.
[*][COLOR="Gray"]Can I do a full install onto USB from the windows installer? Or do I have to go dig up a blank CD somewhere? :p[/COLOR]
[/LIST]

edit: I took a further look at Wubi and yes, it looks like it can install to a USB drive.

---

### Post by Cheesemill on 2013-01-08
> **alnilamski said:**
> Is the browser data (cookies etc.) located entirely within the home directory? **Will selecting "encrypt home directory" be enough to secure the browser data?** This is really my main objective here, is preventing someone who finds the stick from, say, logging into my cookied email.
Yes. All of your user documents and settings are contained within your home directory.
> 

[LIST=1]
[*][COLOR=Gray]Can I do a full install onto USB from the windows installer? Or do I have to go dig up a blank CD somewhere? :p[/COLOR]
[/LIST]
No. You can't use Wubi to do a full installation onto a USB stick. You can either burn an installation DVD or create a separate Live USB stick to run the installation from.

---

### Post by alnilamski on 2013-01-08
> **Cheesemill said:**
> 
No. You can't use Wubi to do a full installation onto a USB stick. You can either burn an installation DVD or create a separate Live USB stick to run the installation from.

So does that mean Wubi's option to "install to USB drive" just means it's creating a liveUSB?

edit: Okay, I burned an installation disc and used it to do a full install to a USB stick as per C.S. Cameron's instructions that you linked to.
It worked. Thanks!

---

