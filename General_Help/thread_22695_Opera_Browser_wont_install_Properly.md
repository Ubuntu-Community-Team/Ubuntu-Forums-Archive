---
title: "Opera Browser wont install Properly"
date: 2005-03-29
forum: General Help
---

### Post by kkathman on 2005-03-29
Just got the Hoary preview. Installed it. Went without a hitch.

However, I want to use Opera instead of Firefox, because its much faster. In my Warty implementation I had no problem D/L the current Opera 7.54, installing it and running it.

However, I did the same with Hoary, and it installs, comes up once. But when you create a launcher for it on the Top Panel and attempt to start it again, it rattles a little then dies and nothing ever comes up.

Any guesses as to why Hoary wouldnt let Opera come up. Its not in the repositories either.

Thanks,
Kork

---

### Post by bailout on 2005-03-29
You may need to install some qt package as Opera uses qt which isn't installed by default on ubuntu.

I can't remember the name but I followed instructions of another thread. Search for install opera or just opera and you should find it. Post again if you can't and I will find details later when I have time.

---

### Post by agenkin on 2005-03-29
Try using the statically linked .deb of Opera (the package name looks opera-static_7.54-20041210.1-qt_en_i386.deb).

---

### Post by kkathman on 2005-03-29
Thanks very much for the reply.

I did install that static package that you recommended. The first time I installed I used a debian package from sarge and indeed I got a qt dependency error.  I remembered and had written in my notes that I needed to get that static one and when I downloaded that one, it installed straight forward, and came up just fine. But when I closed that session down, I was unable to get it back.

One thing that was odd, was that under warty, Opera installed under /usr/bin. Under hoary it didnt. It installed like under where I downloaded the file. That didnt seem right either. Furthermore once it installed, you couldnt do a "whereis opera" or a "which opera" command and have it find it.

This is truly very bizarre.

Anything else I can check?

---

### Post by bailout on 2005-03-29
I used the sarge 7.54u2 deb from opera.com and installed using sudo dpkg -i
If you are on ubuntu and not kubuntu then you will need the qt package installed first;

sudo apt-get install libqt3c102-mt

This worked fine for me. I suggest you uninstall what you have got and try as above. It installs in usr/bin/

---

### Post by kkathman on 2005-03-29
I am assuming that to "uninstall" all I need to do is delete the directories that the other install created?

For instance on my box, I created a subdirectory for downloads where I put everything:  /home/kkathman/downloads.  When I tar'd the tar.gz file from opera, it created this directory under downloads named the same thing as the file name. I then went in and just executed ./opera which did the install.

As far as I could see, all the folders and files were under here as well.

Im unfamilar with the dpkg -i command as Im reasonably new. Do I execute that on the tar.gz file or what?

---

### Post by bailout on 2005-03-29
Ok, I am a total noob as well but the following worked for me. Don't ask me to explain it too much though-I just followed the instructions from another thread :D

If your previous install is just a self-contained folder then I assume you could just delete it or leave it there for the time being.

Go to [www.opera.com](www.opera.com) then download section. 7.54u2 is the latest stable but opera8 beta3 is available if you want. I used 7.54u2 and I will assume you do the same in these instructions, just change the name of the file in the dpkg command if you choose something else. It seemed to read I was on linux and sent me straight to the linux section. If so there will be a dropdown menu for selecting distro, choose debian and then 3.1 sarge.
There is an option for downloading it in tar form but I didn't check it, the deb file is only about 4Mb uncompressed. As it is an install file I think you can just dl and install it from anywhere, I just used /home.

If you are on ubuntu rather than kubuntu then you will need to install the libqt libraries before installing. These are available through synaptic but I am not sure which depository they are in. If you can't find them you will have to enable universe or multiverse. The name of the file you need to install is libqt3c102-mt.

Once you have installed the qt lib you can install opera. Open console and change directory to where you downloaded the file to. ie $ cd /home/ . You can check you are in the right place by typing ls to list the contents of current directory and you should see the opera deb listed. Then type 
$ sudo dpkg -i opera_7.54-20050131.5-shared-qt_en_sarge_i386.deb

If you have dl'ed a different version then obviously use the name of that deb instead.

That is it, opera should now be in the /usr/bin directory. You will have to make a link to it which I don't know how to do in gnome.

There are some issues with opera in linux that I have found so far. The fonts are pretty horrible as standard. It is best to install MS ttf fonts; in synaptic search for msttcorefonts. Also Opera seems to display fonts very small so webpages are difficult to read. Go to tools/preferences/fonts in opera and set the minimum font size to whatever seems best. I have set it to 14 and it seems reasonable.

The Opera for Linux forum at the opera site is good for any further questions on using op under linux.

good luck

---

### Post by wernst on 2005-03-29
Just a footnote:

I installed Opera in Warty (I believe I am the author of the Opera post in the Warty Howto Thread), and it worked fine.

I updated to Hoary and it still worked fine.

I am doing daily dist-upgrades to Hoary and it continues to work fine. Though not my daily browser, it is my daily email client...

gtklp still works as a print agent in opera too...

-Warr

---

### Post by kkathman on 2005-03-29
Thanks very much for all the help.

I deleted the contained directory as was suggested, and then went to the Opera site, downloaded Opera 7.54u and selected the Debian Sarge version. I also didnt check the tar.gz download (which I did before).

Once I downloaded that, I did

sudo apt-get update

sudo apt-get install libqt3c102-mt

sudo dpkg -i <opera deb file that I downloaded>

This worked like a champ.

Thanks for all your help!

---

