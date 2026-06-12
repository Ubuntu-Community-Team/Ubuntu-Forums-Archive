---
title: "Firefox, ubuntu update manager problems..."
date: 2005-08-01
forum: General Help
---

### Post by CrustyDOD on 2005-08-01
OK first FireFox, no matter how many times i try to run it, it simply doesn't start! It shows in bottom menu bar but after a few seconds it disapper. No error no nothing...
In System Monitor i have firefox-bin and its status is: Sleeping

I haven't play with it and i think its stopped working after updating... and this is the second problem! update manager shows that firefox and firefox gnome support are not possible to upgrade! Have no idea why but this is not all! In update manager i have quite a few new updates listed and i already updated them like each day and yet they are still shown in update manager... When i did update, no errors were detected...

So what the hell is going on?

Oh the last thing i did before it broke is install mysql, apache and php with apt-get, no changes made! i think that on the next run, this ain't working anymore, firefox that is, update manager is giving me troubles for a while now!

---

### Post by heimo on 2005-08-01
I'd do something like this:
 ```
killall firefox-bin
ps aux | grep firefox (you should not see firefox process alive)

```
Then try running it again, but this time from terminal to catch any error messages. (just open terminal window and type firefox [enter]).

To get more information and fixing problems on updating packages, you could try:
 ```
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by CrustyDOD on 2005-08-01
ps aux | grep firefox after killall gives me this:
username 10222 0.0 0.0 3032 716 pts/0 R+ 13:15 0:00 grep firefox

This good or not?

if i ran firefox from terminal, i doesn't happen anything, i waited for 1 minute and nothing, no error, no window in menu bar no nothing...

Currently doing apt-get upgrade thingy and its downloading and upgrading the same things as i already did like 10 times, its over 50MB, so slow... let's hope that this time it will upgrade things...

---

### Post by heimo on 2005-08-01
[QUOTE=CrustyDOD]ps aux | grep firefox after killall gives me this:
username 10222 0.0 0.0 3032 716 pts/0 R+ 13:15 0:00 grep firefox
This good or not?
[/QUOTE]
That's good, it's the grep command itself, but no processes with firefox in their name are alive.

[QUOTE=CrustyDOD]
if i ran firefox from terminal, i doesn't happen anything, i waited for 1 minute and nothing, no error, no window in menu bar no nothing...
[/QUOTE]
That's odd. *scratches head* Maybe you could remove and reinstall firefox?

[QUOTE=CrustyDOD]
Currently doing apt-get upgrade thingy and its downloading and upgrading the same things as i already did like 10 times, its over 50MB, so slow... let's hope that this time it will upgrade things...[/QUOTE]
Keep eye on any warnings and errors and post back when you know more.

---

### Post by CrustyDOD on 2005-08-01
No errors on update thingy, think it works now, strange...

ok so firefox now, tried to remove it, no package firefox found error, strange so i did apt-get istall firefox and it shows firefox as NEW package that will be istalled... ok, so i did it and got the following error while unpacking:

```

unpacking firefox (from,....
dpkg: error processing /var/cache/apt/archives/firefox_1.0.6-1ubuntu~5.04ubp1_386.deb (--unpack):
trying to overwrite '/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package mozilla-firefox
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Error were encountered while processing:
/var/cache/apt/archives/firefox_1.0.6-1ubuntu1~5.04ubp1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

That's it... so i tried again by removing 00classic file and the error i get is the same...

---

### Post by heimo on 2005-08-01
You probably want to keep the mozilla-firefox package. I don't know from which repository you're installing firefox package, but that's not in Ubuntu. (sorry for my earlier, not so detailed instructions)

Try (I'm not exactly sure on syntax):
This will **purge/remove/delete** any firefox configuration, possibly plugins too.
```
apt-get remove --purge mozilla-firefox
apt-get install  mozilla-firefox

``` 

After installing, run  
```

which firefox
which mozilla-firefox

``` 
to see which application will be run when you enter that command. Try running the firefox again.

---

### Post by CrustyDOD on 2005-08-01
well guess what, its working now...

thanks man!

---

### Post by Psquared on 2005-09-29
Well, this didn't work for me. Firefox shows two versions. firefox and mozilla-firefox both in /bin. I had to install epiphany to have browsing ability.

I cannot update to Firefox 1.07 and vers 1.06 will not start. Any other ideas??

---

### Post by kb7ypf on 2005-09-30
HI-
[COLOR="DarkRed"]I had the same problem you are having.  What I did was go to each directory and manually deleted the files: [/COLOR]
[B]unpacking firefox (from,....
dpkg: error processing /var/cache/apt/archives/firefox_1.0.6-1ubuntu~5.04ubp1_386.deb (--unpack):
trying to overwrite '/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package mozilla-firefox
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Error were encountered while processing:
/var/cache/apt/archives/firefox_1.0.6-1ubuntu1~5.04ubp1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]
[COLOR="darkred"]
Then I did this for no particular reason:[/COLOR]
apt-get remove --purge mozilla-firefox
apt-get install  mozilla-firefox
[COLOR="darkred"]Then I used the application installer/de-installer program found under administration.  I deinstalled and reinstalled everything that had "firefox" or "mozilla" words in the title.  [/COLOR]
[COLOR="darkred"]I am new to Linux, so I am not sure if all these steps were necessary, but one thing for sure is it did work for me.  
Hope this helps.
Dick[/COLOR]

---

### Post by JimmyBEng on 2005-09-30
you guys may want to also check this [thread](http://www.ubuntuforums.org/showthread.php?t=69050) to see if it shines any light on the problem.  I had problems with firefox starting and notice the two versions of firefox packages on my computer.  here were the steps i took that fixed the problem.
-unintstalled the firefox and mozilla-firefox packages (this also removed some others like ubuntu-desktop and yelp)
-reinstalled only the mozilla-firefox package
-reinstalled ubuntu-desktop and yelp
this got me back to a working firefox.php?t=69050 to see if it shines any light on the problem.  I had problems with firefox starting and notice the two versions of firefox packages on my computer.  here were the steps i took that fixed the problem.
-uninstalled the firefox and mozilla-firefox packages (this also removed some others like ubuntu-desktop and yelp)
-reinstalled only the mozilla-firefox package
-reinstalled ubuntu-desktop and yelp
this got me back to a working firefox

---

