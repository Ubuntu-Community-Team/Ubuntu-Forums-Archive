---
title: "Firefox sometimes want to save php-files to the disk."
date: 2006-11-11
forum: General Help
---

### Post by Anbern on 2006-11-11
I never had this problem with Windows, but now sometimes  when i surf my usual webpages, when i click a link suddenly firefox won't show me the page but instead want to download the php-file. Anyone has anyclue as to why?

---

### Post by aidanr on 2006-11-11
that happens to me occasionally with one site i visit regularly, the site runs vbulletin forum software, usually i just hit cancel and reload and it's fine, i don't know why it happens though:-k

---

### Post by Anbern on 2006-11-11
It doesn't really work for me that way. When this happens it will try to load the php-file for like a minute, and then when i revisit the site like a minute or two later it works just fine again. Very strange.

---

### Post by Popoi on 2007-01-17
Same here... nobody knows how to fix it! :(

---

### Post by majoridiot on 2007-01-17
yup... annoying, aint it?  glad to know we're all suffering together, tho.  seems to be a firefox/swiftfox
bug to me.  opera never does it on my system.

another annoying FF/SF bug... when it hangs on an HTTP upload.  there seems to be no rhyme
or reason to why it does it, but it does it reliably when uploading to my remote server.  again,
opera doesn't do this.

for some reason i choose to suffer with SF, tho.  hehe :-?

---

### Post by hikaricore on 2007-01-17
The only thing I can imagine is happening is corrupt file headers or misread mimetypes.  Firefox sees a php file as a different file type due to either serverside or client side corruption due to packetloss or something of the sort, and does what it's supposed to and opens a save dialog.

I've only seen this happen on heavy traffic sites like neopets for example.

---

### Post by dodgem on 2007-08-23
I'm getting a similar problem...

I have Feisty Fawn installed at home and at work.  At home i have php5, apache2, and mysql5 running so that i can develop a browser based app for work.  Today whilst at work, i updated Ubuntu (hadn't used it here for a while) and copied my files from my usb disk to /var/www/test.  When i tried to look at my app, FF wanted to save my php files to disk when i tried to display them.

I totally removed php, apache, and mysql and reinstalled them.  i saved a file, phptest.php containing the code <?php phpinfo(); ?> in /var/www and that opens fine.  However, any of my files in a subdirectory don't work.  The index.html file opens and renders the frames, but the frame contents (php files) don't load - FF asks to save them.

If i move a php file from the subdirectory to /var/www then firefox will render it.  What's going on??  The same thing happens if i try to open localhost/phpmyadmin as well - FF asks to save the file to disk!

Any help would be appreciated - this is very strange, and annoying :(

Thanks

---

### Post by dbbolton on 2007-09-05
This frequently happens to me when I try to open my UF subscriptions :-?

---

### Post by bleeth on 2008-02-22
I have this trouble: when I'm attempting to parse any .php file by loading it from File Explorer, Firefox wants to save it to disk, not opens it directly. 
My solution is quite simple:
Enter the path to your .php file ([http://localhost/example.php](http://localhost/example.php)) into FF address bar - and it's work great!)

---

### Post by dbbolton on 2008-02-22
Recently, I've had this problem with Epiphany too

---

