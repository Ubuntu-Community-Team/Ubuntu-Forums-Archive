---
title: "firefox update failing"
date: 2006-12-04
forum: General Help
---

### Post by bcp01cui on 2006-12-04
I'm on Dapper and have been attempting to update Firefox (the "firefox" and "firefox-gnome-support" packages) for a couple weeks using the Update Manager and Synaptic.

Each time I get something like this:

<code>
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb)
  Connection failed
</code>

I've eventually been able to update everything else that gets flagged.  I've also tried the <code>sudo apt-get upgrade</code> command, but with the same results.

Any ideas on how to get it to actually work would be much appreciated.

---

### Post by kevinlyfellow on 2006-12-04
have you tried downloading it yourself and then installing?

---

### Post by bcp01cui on 2006-12-04
Do you mean the .deb file those programs are trying to access or the download from Mozilla's web site (something like a .gz, IIRC)?  I was able to download the latter but couldn't make heads or tails of how to install it.

---

### Post by kevinlyfellow on 2006-12-04
I meant the .deb from the ubuntu repos (the one thats linked to in your post).  Just click and try downloading.  BTW what kind of connection do you have?

---

### Post by kevinlyfellow on 2006-12-04
oh there's a script floating around update to ff2 in dapper if you want that:
[http://pykeylogger.sourceforge.net/installnewfirefox.sh](http://pykeylogger.sourceforge.net/installnewfirefox.sh)
download into your home folder and just make it executable and and open your terminal and
sudo ./installnewfirefox.sh

---

### Post by bcp01cui on 2006-12-04
That ended up working...was able to download the .deb with Firefox and open with the default application (had to "sudo apt-get install -f" afterward to fix some dependencies).  Thanks!

---

### Post by bcp01cui on 2006-12-04
By "that" I mean from #4 above, to clarify.

---

### Post by octathlon on 2006-12-05
Thanks, Kevinlyfellow! The script worked great for me. :)

---

### Post by kevinlyfellow on 2006-12-05
The great thing about it is that it seems like its going to work for the latest version of firefox not just 2.0, so don't get rid of it!

---

