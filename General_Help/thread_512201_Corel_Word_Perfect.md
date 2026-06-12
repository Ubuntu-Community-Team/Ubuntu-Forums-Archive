---
title: "Corel Word Perfect"
date: 2007-07-28
forum: General Help
---

### Post by SegMat on 2007-07-28
Hello everyone,

I have been recommending Ubuntu to everyone I know and I have a possible convert from Windows but he loves to run Corel programs.  He hates all other word processors and still runs WordPerfect8.  I'm curious to see if anyone has ever gotten Corel products running in Wine or something similar.  Is it even possible?

Thanks for your help!

Matt

---

### Post by moore.bryan on 2007-07-29
[I]people actually like wordperfect?  i didn't think that was possible...  ;-)
according to a number of websites, wordperfect 8.1 works on linux natively.  downside is you need to purchase it.  i don't know where one would find a wp8.1, but if you can...
[/I]

---

### Post by Smu on 2007-07-29
I'm using corel draw X3 on a virtual XP machine using virtualbox. Apparently newer versions of Corel Draw doesn't work on wine...

---

### Post by SegMat on 2007-07-29
Thanks to both of you for your suggestions, I will likely go for the virtualization one.

Cheers,

Matt

---

### Post by moore.bryan on 2007-07-29
*good luck...*

---

### Post by DOCKIEB on 2007-07-30
You can purchase boxed sets of WordPerfect 8.1 for linux from time to time on ebay. I have purchased three myself for $8.00 each. I have installed it on Linspire 4.5 in the following manner. Using CNR, which is a method of installing linux software which I am told will soon be available to Ubuntu users as the new Linspire 6 is powered by Ubuntu 7.04, install ldso, then libc5, libc6, xlib6, xlib6g, type1inst.  Then from the Corel Linux OS Delux Installation CD, /dists/corellinux-1.0/corel/, install Fonts-115-1.0-4.deb, fonts-16_1.0-5.deb, fonts-69_1.0-4.deb, and then wp-full_8.1-12_i386.deb using the dpkg -i (package name) command in a terminal window.  When Linspire went to its 5x series, a clean install was no longer possible as that series did not support the above x libraries.  A forced install worked but cut off access to CNR. This could be overcome by copying the installation directory, WP8, reinstalling the operating system and then copying WP8 into the new system in its original place. XWP is the command that launches WordPerfect Linux.

I have been trying to find out if Ubuntu 7.04 will support the above libraries without success. If it does, both Linspire 6 and Ubuntu 7.04 should allow a clean installation of Wordperfect 8.1 or at least a forced installation.

---

### Post by waltclay on 2008-04-24
Check out this site for detailed info:  [http://linuxmafia.com/wpfaq/index.html]("http://linuxmafia.com/wpfaq/index.html")

I have been using PC-based word processors since the days of WordStar on CPM and WP is the best. Under 'View' on the menu, check 'Reveal Codes' and you'll see why.

---

### Post by jenuths on 2008-06-14
I have a couple of versions of wp8 for linux, and have managed to get them working on all sorts of linux systems including ones based on AMD64 chips.

The problem is with the libraries, and the loader.

If anyone is still interested, please send me an email at [email]jenuths@homacjen.ab.ca[/email].

---

### Post by konungursvia on 2008-06-17
I love word perfect and use wp11 and 12, have used it since 5.1! Much better than word, in my view.

---

### Post by bpalone on 2008-07-11
Use the virtualization route. I use WP8.1, Quatro Pro 8 and some other Windows Programs in a virtual machine on Hardy Heron.  In fact, virtualization was thing that has allowed me to make the change from Windows.  Can't leave it completely, but I can at least stop the upgrade treadmill.  If it ain't broke, don't fix it. My old versions of software do everything I need. I have threatened to switch to Linux for years, but now I have almost done it.  Still have one computer to go and I'm waiting until I get an important project finished and backed up.

---

