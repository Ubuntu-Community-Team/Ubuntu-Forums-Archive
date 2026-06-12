---
title: "Firefox 3 Beta 4 installation"
date: 2008-03-01
forum: General Help
---

### Post by 3xpl0it on 2008-03-01
Hello,

I am trying to install the new firefox on my machine instead of the old v2.0, but to tell the truth, I don't know howto.

I downloaded:
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-3.0b4pre.en-US.linux-i686.tar.bz2](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-3.0b4pre.en-US.linux-i686.tar.bz2)

and I right clicked on it and un-archived it.

Now, what do I do after this?

Thanks in advance,
-3xpl0it

---

### Post by sumguy231 on 2008-03-01
Now just run the firefox-bin file in the folder you extracted. If you want to install it system-wide, then read these instructions:
[http://kb.mozillazine.org/Installing_Firefox#Linux](http://kb.mozillazine.org/Installing_Firefox#Linux)

---

### Post by hyperair on 2008-03-01
Ah. The trunk installation. Use this script. I made it so that I could get it to automatically update on my system.

```

#!/usr/bin/python

# url to the archive
url = "http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-3.0b4pre.en-US.linux-i686.tar.bz2"

# file name to download to. %s is the date
file = "firefox-3.0b4pre.en-US.linux-i686-%s.tar.bz2"

# temporary directory to use
tmp = '/tmp'

# installation directory to use
installdir = '/opt/firefox-trunk'

import os;
import shutil;
import time;
import sys;

def getTime():
	s = '';
	for i in time.gmtime(time.time())[0:3]:
		s += str(i);
	return(s);

# suffix the filename with the date
file %= getTime();

# change directory to /tmp
os.chdir(tmp);

# remove /tmp/firefox if it exists
if (os.path.isdir('./firefox')):
	shutil.rmtree('./firefox');

# download and extract the package
os.system("wget -c -O '%s' '%s'" % (file,url));
os.system("tar xvjf '%s'" % file);

# check if extraction successful
if (not os.path.isdir('./firefox')):
	sys.stderr.write("Extraction unsuccessful! Please run this script again. If it still fails, then delete %s" % (tmp + '/file'));
	exit(1);

# remove old installation if existent
if (os.path.isdir(installdir)):
	shutil.rmtree(installdir);

# install new minefield	
shutil.move('./firefox',installdir);

# link the minefield plugins folder back to the original
shutil.rmtree(installdir + '/plugins');
os.symlink('/usr/lib/firefox/plugins',installdir + '/plugins');

# link /usr/bin/firefox-trunk to this firefox installation
if (not os.path.islink('/usr/bin/firefox-trunk')):
	os.symlink(installdir + '/firefox','/usr/bin/firefox-trunk');

```

p.s. the above script can only handle .tar.bz2. I also picked that because it's smaller to download.

---

### Post by 3xpl0it on 2008-03-01
> **sumguy231 said:**
> Now just run the firefox-bin file in the folder you extracted. If you want to install it system-wide, then read these instructions:
[http://kb.mozillazine.org/Installing_Firefox#Linux](http://kb.mozillazine.org/Installing_Firefox#Linux)

I tried running the firefox-bin file and it does nothing.  Nothing comes up.  Also, I want to install this where it is on the system globally like the v2.0 firefox is now.  In fact,I basically all I want to do is remove the v2.0 firefox and use the 3.0 one as my default.

> **hyperair said:**
> Ah. The trunk installation. Use this script. I made it so that I could get it to automatically update on my system.

```

#!/usr/bin/python

# url to the archive
url = "http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-3.0b4pre.en-US.linux-i686.tar.bz2"

# file name to download to. %s is the date
file = "firefox-3.0b4pre.en-US.linux-i686-%s.tar.bz2"

# temporary directory to use
tmp = '/tmp'

# installation directory to use
installdir = '/opt/firefox-trunk'

import os;
import shutil;
import time;
import sys;

def getTime():
	s = '';
	for i in time.gmtime(time.time())[0:3]:
		s += str(i);
	return(s);

# suffix the filename with the date
file %= getTime();

# change directory to /tmp
os.chdir(tmp);

# remove /tmp/firefox if it exists
if (os.path.isdir('./firefox')):
	shutil.rmtree('./firefox');

# download and extract the package
os.system("wget -c -O '%s' '%s'" % (file,url));
os.system("tar xvjf '%s'" % file);

# check if extraction successful
if (not os.path.isdir('./firefox')):
	sys.stderr.write("Extraction unsuccessful! Please run this script again. If it still fails, then delete %s" % (tmp + '/file'));
	exit(1);

# remove old installation if existent
if (os.path.isdir(installdir)):
	shutil.rmtree(installdir);

# install new minefield	
shutil.move('./firefox',installdir);

# link the minefield plugins folder back to the original
shutil.rmtree(installdir + '/plugins');
os.symlink('/usr/lib/firefox/plugins',installdir + '/plugins');

# link /usr/bin/firefox-trunk to this firefox installation
if (not os.path.islink('/usr/bin/firefox-trunk')):
	os.symlink(installdir + '/firefox','/usr/bin/firefox-trunk');

```

p.s. the above script can only handle .tar.bz2. I also picked that because it's smaller to download.

Sorry, but I am a noob to this stuff, and I really don't how that works.  I see it downloads the whole thing and updates it every time you run the script, but how do I compile that or save that?

Thanks everyone
-3xpl0it

---

### Post by hyperair on 2008-03-01
It doesn't redownload the whole thing every time you run the script. It passes the "-c" flag to wget, so that download resuming occurs if it is interrupted. What you should do is open your text editor (Applications->Accessories->Text Editor), Copy and paste that in, and save it anywhere you want. Say, your HOME directory (/home/<username>)

Then, give it execute permissions. Right click on the file, and click properties. In the permissions tab, make sure the "Allow executing as program" is checked. Then you can run the script from terminal (if you want to monitor it) or from the run dialog (if you want it to run in background).
```

sudo ~/<script name>

```

Replace <script name> with whatever you've saved the script as.

---

### Post by hyperair on 2008-03-01
It doesn't redownload the whole thing every time you run the script. It passes the "-c" flag to wget, so that download resuming occurs if it is interrupted. What you should do is open your text editor (Applications->Accessories->Text Editor), Copy and paste that in, and save it anywhere you want. Say, your HOME directory (/home/<username>)

Then, give it execute permissions. Right click on the file, and click properties. In the permissions tab, make sure the "Allow executing as program" is checked. Then you can run the script from terminal (if you want to monitor it) or from the run dialog (if you want it to run in background).
```

sudo ~/<script name>

```

Replace <script name> with whatever you've saved the script as.

---

### Post by 3xpl0it on 2008-03-02
> **hyperair said:**
> It doesn't redownload the whole thing every time you run the script. It passes the "-c" flag to wget, so that download resuming occurs if it is interrupted. What you should do is open your text editor (Applications->Accessories->Text Editor), Copy and paste that in, and save it anywhere you want. Say, your HOME directory (/home/<username>)

Then, give it execute permissions. Right click on the file, and click properties. In the permissions tab, make sure the "Allow executing as program" is checked. Then you can run the script from terminal (if you want to monitor it) or from the run dialog (if you want it to run in background).
```

sudo ~/<script name>

```

Replace <script name> with whatever you've saved the script as.

Ok I have your script working and I ran it in the terminal and downloaded the latest trunk...  Now, how do I run Firefox itself?

---

### Post by rolor on 2008-03-07
Maybe this is a stupid question, but why do you go through all this effort? Is the latest beta very important to you?
You can also just install Firefox-3.0 through Synaptic for example and use beta3 until beta4 will be provided.

On a side note: home grown Firefoxes will use your default profile and can possibly corrupt it. Switching back to FF2 could be a problem then, just so you know.

---

### Post by hyperair on 2008-03-07
Run in the run dialog "firefox-trunk". That should start it. There's just one problem with the script. Every time a new release comes out, the URL to download the archive changes. So you need to change it at the top of the script. This particular line:
```
url = "http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-3.0b4pre.en-US.linux-i686.tar.bz2"
```

@rolor: Some people like to follow the development of software you know. Either way Firefox's trunk development is rather stable compared to some other software which is why I dare to update daily and use it as my primary browser.
Also, when running firefox, you can use a separate profile so that you don't corrupt the original profile. 
```
firefox-trunk -ProfileManager
```

---

### Post by 3xpl0it on 2008-03-08
> **hyperair said:**
> Run in the run dialog "firefox-trunk". That should start it. There's just one problem with the script. Every time a new release comes out, the URL to download the archive changes. So you need to change it at the top of the script. This particular line:
```
url = "http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-3.0b4pre.en-US.linux-i686.tar.bz2"
```

@rolor: Some people like to follow the development of software you know. Either way Firefox's trunk development is rather stable compared to some other software which is why I dare to update daily and use it as my primary browser.
Also, when running firefox, you can use a separate profile so that you don't corrupt the original profile. 
```
firefox-trunk -ProfileManager
```

Thanks, sorry for the long reply, I'll try later tonight.

---

### Post by 3xpl0it on 2008-03-09
Ok, I seriously cannot get this to work lol.  Everytime I run the firefox file, it opens up my v2.0 firefox, even though im running the file in the v3.0Beta5 directory.

1. How do I run this program without it running my v2.0 firefox?
2. For some reason I have a firefox-trunk file in my opt directory and I cannot remove it even using "sudo rm -d firefox-trunk"

please help,
-3xpl0it

EDIT: Got #1!

I am running FF3.0Beta5, and the way I did it was by opening up firefox and removing this:

> if [ $found = 0 ]; then
  # Check default compile-time libdir
  if [ -x "$moz_libdir/run-mozilla.sh" ]; then
    dist_bin="$moz_libdir"
  else 
    echo "Cannot find mozilla runtime directory. Exiting."
    exit 1
  fi
fi

Still need help with question #2

Thanks everyone
-3xpl0it

---

### Post by hyperair on 2008-03-10
The script I wrote installs firefox into a folder called /opt/firefox-trunk. That's probably what you're seeing. To remove it (uninstall firefox 3.0 beta 5 pre) remove the folder.
```
sudo rm -rf /opt/firefox-trunk
```

As for #1: You don't need that script. All you need to do is run "firefox-trunk" instead of "firefox". Change your default browser in System->Preferences->Preferred Applications also.

Also, if you've read my script properly, you'd have realized that there are some variables at the top where you can change the URL of firefox's archive, and also the directory it is installed to.

---

### Post by 3xpl0it on 2008-03-10
> **hyperair said:**
> The script I wrote installs firefox into a folder called /opt/firefox-trunk. That's probably what you're seeing. To remove it (uninstall firefox 3.0 beta 5 pre) remove the folder.
```
sudo rm -rf /opt/firefox-trunk
```

As for #1: You don't need that script. All you need to do is run "firefox-trunk" instead of "firefox". Change your default browser in System->Preferences->Preferred Applications also.

Also, if you've read my script properly, you'd have realized that there are some variables at the top where you can change the URL of firefox's archive, and also the directory it is installed to.

yes, I did change that to firefox beta 5 :)

Thanks,
-3xpl0it

EDIT: How might I go about removing FF2.0 and installing FF3.0 globally?

---

### Post by hyperair on 2008-03-10
Firefox 2.0... I'm not very sure, because I'm using Ubuntu Hardy and you're probably not. Over here the default Firefox is 3.0, but it's a "stable" beta, not a trunk beta (prebeta)

---

### Post by green_earth on 2008-03-12
Please forgive, but I just downloaded the latest firefox beta and wanted to install it on my linux box instead of trying it out on windows. While I've been loving Ubuntu, I have to say if anyone out there wants an example of why so many people get frustrated with Linux and go back to windows, this thread is a great example. The amount of agony for someone like me to install a program that is not in the default ubuntu repository (add/remove) is mind-boggling. 99% of computer users are not up to speed on code and terminal commands, and never will be! Why can't the linux standard base people get past this kind of GARBAGE! Yes, yes, I know there are .deb and .rpm files out there. But most of what I find is this tar.gz stuff. Perhaps some of you will get angry with my ignorance and lack of understanding of the freedom open code and terminal commands give - and I don't want to take that away from anyone. Just help us boneheads out, I want, I truly want to throw M$ under the bus for ever, but until I can run in a GUI and install what I want when I want (like windows), I just can't give up a 95% GUI run operating system like windows.... yet. Forgive my rant...

---

### Post by hyperair on 2008-03-12
I'd really like to say something in defence of Ubuntu and other Linux distros, but yeah you've got a point.

---

### Post by OrangeCrate on 2008-03-12
> **hyperair said:**
> I'd really like to say something in defence of Ubuntu and other Linux distros, but yeah you've got a point.

+1

---

### Post by copyleft on 2008-03-12
I found that this worked like a charm:

[http://tombuntu.com/index.php/2008/03/11/install-firefox-3-beta-4-in-ubuntu-with-one-command/](http://tombuntu.com/index.php/2008/03/11/install-firefox-3-beta-4-in-ubuntu-with-one-command/)

---

### Post by the lah on 2008-03-12
> **copyleft said:**
> I found that this worked like a charm:

[http://tombuntu.com/index.php/2008/03/11/install-firefox-3-beta-4-in-ubuntu-with-one-command/](http://tombuntu.com/index.php/2008/03/11/install-firefox-3-beta-4-in-ubuntu-with-one-command/)

I used this and it works , but my problems are with the mplayer plug-in or totem plug ins not working with beta 4 ( the flash works ) but playing other movie files wont work.

---

### Post by copyleft on 2008-03-13
My plugins were also not being recognized in "about:plugins" (typed in the address bar) in 3.0b4  

Apologies if this is not the straight forward fix you might be looking for - I'm pretty noob... but after fiddling with this in the terminal for an hour, here's how I fixed this problem.

After following the instructions at 

[http://tombuntu.com/index.php/2008/0...h-one-command/](http://tombuntu.com/index.php/2008/0...h-one-command/)

I went to my home folder and collected any plugin file (in my home folder, there were a bunch of these not inside any folder - they have a ".so" file extension) and copy and pasted these into my /home/your-name/firefox/plugins folder in my home directory.  

Everything works now and under "about:plugins", all plugins are listed accordingly.  

I'm sure someone more experienced could devise some fix with just a line or two for the terminal.

Hope this helps!

---

### Post by Tu13erhead on 2008-03-13
> **green_earth said:**
> Please forgive, but I just downloaded the latest firefox beta and wanted to install it on my linux box instead of trying it out on windows. While I've been loving Ubuntu, I have to say if anyone out there wants an example of why so many people get frustrated with Linux and go back to windows, this thread is a great example. The amount of agony for someone like me to install a program that is not in the default ubuntu repository (add/remove) is mind-boggling. 99% of computer users are not up to speed on code and terminal commands, and never will be! Why can't the linux standard base people get past this kind of GARBAGE! Yes, yes, I know there are .deb and .rpm files out there. But most of what I find is this tar.gz stuff. Perhaps some of you will get angry with my ignorance and lack of understanding of the freedom open code and terminal commands give - and I don't want to take that away from anyone. Just help us boneheads out, I want, I truly want to throw M$ under the bus for ever, but until I can run in a GUI and install what I want when I want (like windows), I just can't give up a 95% GUI run operating system like windows.... yet. Forgive my rant...

No offense, but if you can't perform relatively basic Linux tasks, you probably shouldn't be installing (possibly unstable) development builds of software.

There's a reason why stuff makes it into the repositories.

---

### Post by hyperair on 2008-03-13
This is merely an example. There are many more software which don't come in deb files, and aren't in any repository. They just let you download a .tar.gz file with installation instructions in them. Quite annoying if you ask me. I prefer debs.

---

### Post by green_earth on 2008-03-14
Tu13erhead, you may be right in your warning! However, there are hundreds of thousands of folks who don't know basic linux tasks who are downloading and installing the beta on windows and mac computers. I've taken my chances for at least 10 years with several different types of beta software on Windows - including Mozilla Phoenix since version 0.5, then Firebird, and now Firefox. Although I can't claim I've not had some late nights fixing issues, I've made it by just fine with windows commands via the gui driven dialogs. I believe Linux has a great and marvellous future - but until someone, somewhere gains _significant influence_ in the Linux community who thinks a little bit like Jobs or Gates (what the customer wants) instead of like a programmer (historically Linux's real customers), Linux will remain at >5% of the market. Yeah, I know they were and are driven by world domination and money, but they've gotten the world to be familar with what an .exe, C drive, or .doc is - don't you think? Anyway, I should dedicate more time to learning linux commands, which will only benefit me in the future. So, your point is well taken. Best...

---

