---
title: "How to get Adobe Acrobat Reader to Work"
date: 2007-05-19
forum: General Help
---

### Post by Goliath! on 2007-05-19
I tried to use the standard pdf readers (Evince and KPDF) but I couldn't get used to them.  Some pdfs didn't display correctly, and it was hard to copy text out of the pdfs.  So I decided I needed to have authentic Acrobat Reader.

This thread gives some good instructions on how to install the Reader: [http://ubuntuforums.org/showthread.php?t=446702]("http://ubuntuforums.org/showthread.php?t=446702")
However, it didn't work for me.  When I clicked on Applications > Office > Adobe Reader, nothing happened.  I checked, and the launcher executes acroread.  So I tried to execute that from the command line and I got a screen full of this: 
```
expr: syntax error
expr: syntax error
expr: syntax error
expr: syntax error
expr: syntax error
```

I looked in the forums and couldn't find anything.  acroread is just a shell script.  So I started delving into the code.  It took me a while but I fould out how to fix the problem.

Do to a terminal window and try this:
```
me@laptop:~/adobe$ which acroread
```
This will tell you where the file acroread is.  The results will probably be /usr/bin/acroread.  However, is that the real file?  Do a long ls on it and you'll see something like this:
```
me@laptop:~/adobe$ ls -l /usr/bin/acroread
lrwxrwxrwx 1 root root 40 2007-05-19 00:51 /usr/bin/acroread -> /usr/local/Adobe/Acrobat7.0/bin/acroread
```.

So /usr/bin/acroread is nothing but a symbolic link to /usr/local/Adobe/Acrobat7.0/bin/acroread.  Do an ls -l on that file and you'll see it's the real file.

You'll need to edit and write to that file, so you'll need admin rights.  You can use gedit or whatever; I can't give up vi.  You'll want to do something like this:
```
me@laptop:~/adobe$ sudo gedit /usr/local/Adobe/Acrobat7.0/bin/acroread
```

Now once you've got that file open, go to about line 405 and you'll see this rather dubious code:
```
get_gtk_file_ver()
{
        if [ -f "$1" ]; then
        if [ -h "$1" ]; then
                ifile=`readlink $1`
                    if [ $? -eq 1 ]; then
                                return 1
                fi
        fi

                mfile=`basename $ifile`
        echo $mfile | grep -q "libgtk-x11-\([0-9]*\).0.so.0.\([0-9]*\).\([0-9]*\)" 2>/dev/null

                if [ $? -ne 0 ]; then
           return 1
        fi
. . .

```

I didn't take the time to try to debug Adobe's logic.  I just found a way to fix it.  You'll add one echo statement at line 5 of that function.  The whole function will look like this:
```
get_gtk_file_ver()
{
        if [ -f "$1" ]; then
        if [ -h "$1" ]; then
echo XXX this one echo makes it work
                ifile=`readlink $1`
                    if [ $? -eq 1 ]; then
                                return 1
                fi
        fi

                mfile=`basename $ifile`
        echo $mfile | grep -q "libgtk-x11-\([0-9]*\).0.so.0.\([0-9]*\).\([0-9]*\)" 2>/dev/null

                if [ $? -ne 0 ]; then
           return 1
        fi

                echo $mfile| sed 's/libgtk-x11-\([0-9]*\).0.so.0.\([0-9]\)00.\([0-9]*\)\|\(.*\)/\1\2\3/g'
        return 0
    fi

    return 1
}

```

You won't see that echo when you run Acrobat but at least it solved my problem.

Presumably, the script must work in most cases; I can't believe Adobe's code has such an obvious problem and it hasn't been corrected.  So this must be something in my system that causes their logic to fail.  My configuration is as follows:
[LIST]
[*]Dell D610 laptop
[*]Installed adobe by downloading AdobeReader_enu-7.0.9-1.i386.tar.gz from adobe.com.
[*]Ubuntu version below
[/LIST]
```
me@laptop:~/adobe$ cat /proc/version
Linux version 2.6.20-15-386 (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 Sun Apr 15 07:34:00 UTC 2007
```

I will point Adobe's support to this post as well.

I hope this helps some one!

---

### Post by raja on 2007-05-19
Funny that I had acrobat working, but just found today that it failed to launch. Starting acroread from the terminal gives the same error as you. I would like to try your solution, but I dont understand what you are trying to do. Why does adding that line work? 
I prefer to understand what I am doing before doing it.

---

### Post by Goliath! on 2007-05-20
I didn't bother to trace thru all of Adobe's bad code.  But those two if statements right together lead me to believe they didn't think thru all the conditional possibilities.  Someplace they messed up their ifs and fis and statement blocks.  

The code tries to find out where the gtk library is, and they're trying to handle the case where it might be symbolic link.  The if -f checks to see if the file is a regular file (not a directory).  Then the if -h checks to see if the file is a link.  If the file were a directory, their code would fail entirely.

Putting in that extra statement (that doesn't do anything materially) doesn't correct the logic.  It just makes it work for me, given my particular environment (placement of gtk library).  I think the bash if may have some intricacies about single-statement statement blocks after an if.

Looking at the postings on the Adobe site, it seems like Adobe has also messed up their expr statements.  It's not worth my time to sift through their errors right now.  And frankly it's been too long since I've strolled through the intricacies of shell programming.  Maybe if Adobe wanted to cut me a check I could fix it for them, though :)

---

### Post by raja on 2007-05-20
Well - it worked.
I see that the line produces an error and maybe prevents the get_gtk_version function from completing its work. But I still could not figure out where the error is. 
Thanks for the tip anyway.

---

### Post by kc2005 on 2007-05-28
Nice tip! Thank you.

---

### Post by JohnnyBee on 2007-05-31
Goliath, thanks indeed your tip solved a major problem of mine, since I read a lot of pdfs.

Thanks again!!!:D

---

### Post by amersault on 2007-06-01
and for those wanting the easy route, you can also install the Reader via Automatix2.

---

### Post by lowracer on 2007-06-05
That fixed it for me.  Thanks.

---

### Post by missaka on 2007-06-06
A more elegant fix for the problem is as follows:

In function get_gtk_file_ver():

The line that reads:
echo $mfile| sed 's/libgtk-x11-\([0-9]*\).0.so.0.\([0-9]\)_00_.\([0-9]*\)\|\(.*\)/\1\2\3/g'
should be
echo $mfile| sed 's/libgtk-x11-\([0-9]*\).0.so.0.\([0-9]\)_000_.\([0-9]*\)\|\(.*\)/\1\2\3/g'

The number of 0's following '1' should match what the real libgtk is: libgtk-x11-2.0.so.0.1_000_.8

---

### Post by tminuszero on 2007-06-06
Thanks missaka - that seems to have solved my problem!

---

### Post by lognok on 2007-06-07
I just downloaded the reader from Adobes site and ran the installer. I accepted all the default settings and now I have Adobe Reader 7 installed with browser plugin (optional during install) and a menu lanuch button.
Didn't take more than 5min to install, although the download was a little heavy (42MB tar.gz).

---

### Post by le_jawa on 2007-06-12
Maybe I'm just a tad naive, but isn't it all just a ton easier to install the "acroread' package via Add/Remove, Synaptic or aptitude?  I think you have to enable the Multiverse repository (or maybe it was Commercial), but the package works just fine right out of the box.

Just a thought,

Jason

---

### Post by Goliath! on 2007-06-12
I can always count on the open source community to show me how much I have to learn.

And I thought I was being so helpful.

Oh well, I enjoyed the debugging experience :)

---

### Post by dxturner on 2007-06-20
The problem occurs when you have an updated gtk package that has more than one digit in the middle of the version number ... so gtk v 2.9.xxx works, but 2.10.xxx don't!

if you've got gkt 2.1x.xxx you'll need to fix line 418 so that the regex works ... see the forum note on the adobe site:
[http://www.adobeforums.com/cgi-bin/webx/.3bc435f2](http://www.adobeforums.com/cgi-bin/webx/.3bc435f2)

Line 418 in the acroread script was:

echo $mfile| sed 's/libgtk-x11-\([0-9]*\).0.so.0.\([0-9]\)00.\([0-9]*\)\|\(.*\)/\1\2\3/g'

but should be:

echo $mfile| sed 's/libgtk-x11-\([0-9]*\).0.so.0.\([0-9][COLOR="Red"]*[SIZE="2"]*[/SIZE]*[/COLOR]\)00.\([0-9]*\)\|\(.*\)/\1\2\3/g'

( note the asterisk ' * ' in the second regex ) ... I didn't come up with this solution, just passing it along!

---

### Post by stchman on 2007-06-20
I installed Acrobat Reader 7 from the Medibuntu repositories and it works great.

[http://www.stchman.com/install_adobe.html](http://www.stchman.com/install_adobe.html)

Worked for me.

---

### Post by FerhatBingol on 2007-06-26
Same problem, same computer, same version, same fix...

Thank you !...

---

### Post by felix.rommel on 2007-07-05
Thanks for your tips! :)

Gutsy Tribe-2 + current updates:

@Goliath!: your solution worked
@missaka: your solution did not work
@dxturner: your solution was already implemented in medibuntu acroread version but did not work

---

### Post by ayates on 2007-07-06
Ditto with the thanks.
Goliath!'s worked for me.

---

### Post by Icarosaurus on 2007-07-07
Worked as a charm for me, with dxturner solution.
Thank you

---

### Post by Oxygene on 2007-07-15
This is some pretty weird code. 
The problem with my (gutsy) installation was the following:

```
$ locate libgtk-x11
/usr/lib/libgtk-x11-2.0.so
/usr/lib/libgtk-x11-2.0.la
/usr/lib/libgtk-x11-2.0.a
/usr/lib/libgtk-x11-2.0.so.0
/usr/lib/libgtk-x11-2.0.so.0.1105.0
```

The regexp checks for a number suffixed by two zeros, which is apparently not the case with "1105". I replaced the "00" with "[0-9]\{2\}" and it worked.

The line now reads
```
echo $mfile| sed 's/libgtk-x11-\([0-9]*\).0.so.0.\([0-9]*\)[COLOR="Red"][0-9]\{2\}[/COLOR].\([0-9]*\)\|\(.*\)/\1\2\3/g'
```

---

### Post by wirawan0 on 2007-07-17
For those who care for absolute correctness: the more correct patch is available online, here:

[http://remi.collet.free.fr/files/acroread.patch](http://remi.collet.free.fr/files/acroread.patch)

Download the patch, and patch the acroread using it.

The way to do it: suppose you download the patch to /tmp/acroread.patch, then:

$ sudo bash
(asking your password then...)

# cd /usr/local/Adobe/Acrobat7.0/bin
# patch < /tmp/acroread.patch
# exit

Now invoke acroread, it should work OK whether the libgtk file was libgtk-x11-2.0.so.0.1000.11 or the old-style libgtk-x11-2.0.so.0.200.0  .

I found a comprehensive discussion here:

[http://www.adobeforums.com/cgi-bin/webx?128@@.3bc22d86](http://www.adobeforums.com/cgi-bin/webx?128@@.3bc22d86)

HTH,
Wirawan

---

### Post by haopeng on 2007-07-20
> **dxturner said:**
> The problem occurs when you have an updated gtk package that has more than one digit in the middle of the version number ... so gtk v 2.9.xxx works, but 2.10.xxx don't!

if you've got gkt 2.1x.xxx you'll need to fix line 418 so that the regex works ... see the forum note on the adobe site:
[http://www.adobeforums.com/cgi-bin/webx/.3bc435f2](http://www.adobeforums.com/cgi-bin/webx/.3bc435f2)

Line 418 in the acroread script was:

echo $mfile| sed 's/libgtk-x11-\([0-9]*\).0.so.0.\([0-9]\)00.\([0-9]*\)\|\(.*\)/\1\2\3/g'

but should be:

echo $mfile| sed 's/libgtk-x11-\([0-9]*\).0.so.0.\([0-9][COLOR="Red"]*[SIZE="2"]*[/SIZE]*[/COLOR]\)00.\([0-9]*\)\|\(.*\)/\1\2\3/g'

( note the asterisk ' * ' in the second regex ) ... I didn't come up with this solution, just passing it along!
Hi dxturner, I also has the "syntax error" for acroread, I've done the same fix on my ubuntu,
why it still not working for me?

I changed the said line to all the following suggested solutions from this thread,

echo $mfile| sed 's/libgtk-x11-\([0-9]*\).0.so.0.\([0-9]*\)[0-9]\{2\}.\([0-9]*\)\|\(.*\)/\1\2\3/g'
echo $mfile| sed 's/libgtk-x11-\([0-9]*\).0.so.0.\([0-9]\)000.\([0-9]*\)\|\(.*\)/\1\2\3/g'
echo $mfile| sed 's/libgtk-x11-\([0-9]*\).0.so.0.\([0-9]*\)00.\([0-9]*\)\|\(.*\)/\1\2\3/g'

They all not working for me. /usr/bin/acroread does not throw any error it just return with nothing showing after I run. Can you help? Thanks!

my gtk version is 
# dpkg -l |grep gtk
ii  gtk2-engines                               2.10.1-0ubuntu1                        theme engines for GTK+ 2.x
ii  gtk2-engines-pixbuf                        2.10.11-0ubuntu3                       Pixbuf-based theme for GTK+ 2.x
ii  gtk2-engines-ubuntulooks                   0.9.12-4                               'ubuntulooks' theme for GTK+ 2.x

---

### Post by martin28 on 2007-07-22
Hello,

I'm running Fiesty Fawn and I'm an Ubuntu beginner.  I can't get Acrobat to work.

I installed Acrobat using the .rpm from the site which I converted to .deb using alien.  I did it like this because I found a thread that said that was the way to do it.

Then when I tried to run it I got a permission error.  When I went to Applications->Office->Adobe Reader and clicked on it I got a messsage that said "Failed to execute child process "acroread" (Permission denied)".

So I googled and found a site that said you had to run  sudo chmod 755 /usr/bin/acroread.

I did that and now when I doubleclick on Adobe Reader nothing happens!!  I've tried it in the terminal and nothing happens there either, it returns nothing and i'm back to the command prompt.

I've tried changing all the stuff in the thread, about the missing '0' from line 418, but still nothing works.

If anybody has the time/interest to help me get this working I would be very grateful!!

Thanks,
Martin.

---

### Post by raja on 2007-07-22
> **martin28 said:**
> Hello,

If anybody has the time/interest to help me get this working I would be very grateful!!

Thanks,
Martin.

Hi,
I recently installed from the adobe site with the shell script with no problems. Anyway - what is the output of ```
acroread
```
and ```
cd /usr/bin
./acroread
```

---

### Post by Goliath! on 2007-07-22
@Martin28, you might also trying to install Acrobat reader thru Automatix.  Instructions are here: [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

---

### Post by raja on 2007-07-22
> **Goliath! said:**
> @Martin28, you might also trying to install Acrobat reader thru Automatix.  Instructions are here: [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

Not a very good idea to use automatix for something that can be pretty easily done without it. 
Remember that Automatix is not recommended by the Ubuntu team and has caused problems when people upgrade.

---

### Post by felix.rommel on 2007-07-26
Since a few days even Goliath's: method does not work any more. acroread  has the following output on command line:

(acroread:5771): Gtk-CRITICAL **: gtk_rc_get_style: assertion `GTK_IS_WIDGET (widget)' failed

Any idea what could cause that error?

---

### Post by mwiertz on 2007-07-26
bump! same problem here

---

### Post by peteryuan301 on 2007-07-29
the same problem,all solutions are not work ,my os is 7.04
> #locate libgtk-x11
/usr/lib/libgtk-x11-2.0.so.0
/usr/lib/libgtk-x11-2.0.a
/usr/lib/libgtk-x11-2.0.la
/usr/lib/libgtk-x11-2.0.so.0.1000.11
/usr/lib/libgtk-x11-2.0.so

---

### Post by felix.rommel on 2007-07-29
> **felix.rommel said:**
> Since a few days even Goliath's: method does not work any more. acroread  has the following output on command line:

(acroread:5771): Gtk-CRITICAL **: gtk_rc_get_style: assertion `GTK_IS_WIDGET (widget)' failed

Any idea what could cause that error?

Sorry, I'm in the wrong forum - thought this is Gutsy development forum - so my problems with Acroread on Gutsy are different then yours on Feisty.

For Feisty users I recommend using Medibuntu repository ([http://www.medibuntu.org/repository.php):](http://www.medibuntu.org/repository.php):)

```

echo "deb http://de.packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list
wget -q http://de.packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install acroread
```

Should do the trick for installing Adobe Reader 7.0. Medibuntu offers also interesting packages like Skype, Google Earth and video codecs!

---

### Post by edmonster on 2007-08-04
Thanks Missaka!!

---

### Post by kroetenmist on 2007-08-19
Hi,

i have the same problem with adobe acrobat reader in gutsy.

> (acroread:10130): Gtk-CRITICAL **: gtk_rc_get_style: assertion `GTK_IS_WIDGET (widget)' failed

i just made a bug reprt at launchpad.

[https://bugs.launchpad.net/ubuntu/+bug/133464](https://bugs.launchpad.net/ubuntu/+bug/133464)

---

### Post by jkrroemer on 2007-08-21
Thanks both of you. It works. I prefer using missaka solution but Goliath! worked as well. I only prefer the missaka solution due the explanation makes sense. 
Well, I appreciate your efforts - couldn't make it work - so thanks very much.
jkrroemer

---

### Post by prand25 on 2007-08-28
Unable to unlock list directory-see paste:


prandy@prandy-desktop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O/etc/apt/sources.list.d/medibuntu.list
--19:17:40--  [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.10
Connecting to www.medibuntu.org|87.98.242.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 233 [text/plain]

100%[=================================================================================>] 233           --.--K/s             

19:17:45 (9.95 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [233/233]

prandy@prandy-desktop:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US          
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources                                  
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US         
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release
  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Get:5 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release [2195B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages                                                                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages                                                                  
Fetched 2387B in 6s (371B/s)                                                                                                
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
prandy@prandy-desktop:~$ run apt-get update
bash: run: command not found
prandy@prandy-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
prandy@prandy-desktop:~$

---

### Post by felix.rommel on 2007-08-29
@prand25:

You should copy and paste the 3 lines which I posted in comment [#30]("http://ubuntuforums.org/showpost.php?p=3098301&postcount=30"). They must be inserted one after the other so that you have 3 steps.

But in _your case_ you _only_ have to do the following _2 steps_ cause you already have done the first one. Copy each line exactly with copy and paste in your Terminal:

```
wget -q http://de.packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install acroread
```

Some additional information for updating your package archive:

> prandy@prandy-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

You must run apt-get as super user (root) when doing an update:

```
sudo apt-get update
```

---

### Post by hanover.fiste on 2007-09-04
> **missaka said:**
> A more elegant fix for the problem is as follows:

In function get_gtk_file_ver():

The line that reads:
echo $mfile| sed 's/libgtk-x11-\([0-9]*\).0.so.0.\([0-9]\)_00_.\([0-9]*\)\|\(.*\)/\1\2\3/g'
should be
echo $mfile| sed 's/libgtk-x11-\([0-9]*\).0.so.0.\([0-9]\)_000_.\([0-9]*\)\|\(.*\)/\1\2\3/g'

The number of 0's following '1' should match what the real libgtk is: libgtk-x11-2.0.so.0.1_000_.8

That didn't fix it for me. But using 

echo $mfile| sed 's/libgtk-x11-\([0-9]*\).0.so.0.\([0-9]\)*.\([0-9]*\)\|\(.*\)/\1\2\3/g'

did. I decided that since the number of 0's could change, I'd just wild card it.

---

### Post by fakie_flip on 2007-09-09
It works except buggy. I got many errors. Why is this happening? Also I have attached a screenshot. Adobe reader comes up, but it's running with a lot of errors. Please help.

```
chris@ubuntu:~/Desktop$ acroread 
[: 646: XXX this one echo makes it work: bad number
[: 646: this: unexpected operator

(acroread:16482): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
chris@ubuntu:~/Desktop$ 
```

---

### Post by Goliath! on 2007-09-09
If you go to the Adobe forums and search for that error message about PPKLite you'll find several posts where adobe shows you how to NOT load that library if you don't need it.  That doesn't solve the root cause, but I suppose if you're satisfied with that approach it will get you up and running.

I would suggest trying one of the other approaches in this thread.  I have not tried it but I like the idea of installing it from mediubuntu.  There are instructions above.

Another way to install from Mediubuntu is to use the auto-generated sources file from this page: [http://www.ubuntu-nl.org/source-o-matic/]("http://www.ubuntu-nl.org/source-o-matic/")

Let us know if you still have problems.

---

### Post by aditya.rachakonda on 2007-09-29
@Martin28, I wanted the latest Acrobat Reader so I tried your method and it worked. Downloaded the Adobe Reader 8.1.1's .rpm, did an alien (with --scripts option) and got the .deb. I had to add it to my menu manually.
Hope this works for others too.

For everybody who is arguing for evince, I think it has problems with antialiasing and also gradients. So some old pdf's look terrible and pdf's created using beamer (a latex presentation tool) render poorly. That's why I need Adobe Reader some times - though it is very slow in comparison.

-Aditya

---

### Post by felix.rommel on 2007-09-29
> **aditya.rachakonda said:**
> @Martin28, I wanted the latest Acrobat Reader so I tried your method and it worked. Downloaded the Adobe Reader 8.1.1's .rpm, did an alien (with --scripts option) and got the .deb. I had to add it to my menu manually.
Hope this works for others too.

@ALL: Adobe offers it's Adobe Reader 8.1.1 in native deb format! This also runs on Gutsy. You do NOT need Alien any more:

Go to the following site and choose deb as your version:

[http://www.adobe.com/products/acrobat/readstep2_allversions.html](http://www.adobe.com/products/acrobat/readstep2_allversions.html)

Then download the deb file and install it with (replace XYZ with the name of downloaded package):

```
dpkg --install XYZ
```

Or click in Nautilus on it and install it graphically.

---

