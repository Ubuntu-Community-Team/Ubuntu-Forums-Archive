---
title: "How do I install new software?"
date: 2007-06-06
forum: General Help
---

### Post by dude1234 on 2007-06-06
I'm new to Ubuntu. I had an issue getting my internet connection and had to disable ipv6. Internet now works fine. Then I couldn't get evolution email to talk to my mail server. I decided to install Thunderbird. Downloaded it at work and copied the files over. Used the ubuntu archiver to unzip them. Went to the menu item to install and got a message that it wants to check what new programs are available. Says it can't check because the log is out of date. Says it can't update the log because it can't get onto the internet.

Can I just install Thunderbird without all this piffle about some log that can't be found?

---

### Post by renzokuken on 2007-06-06
thunderbird is in the repos.......if your internet is working run the following

```
sudo apt-get update
sudo apt-get install mozilla-thunderbird
```

EDIT: FYI, most linux programs are in the ubuntu repos and can be easily installed using Synaptic, which is in System -> Admin -> Synaptic Package Manager (i'm assuming you are using gnome here)

---

### Post by pn4577 on 2007-06-06
Hi dude1234,

if your internet connection is available, installing software without trouble should be possible with ```
sudo apt-get install <package-name>
``` or via gui package managers like adept or synaptic. Installing self-copied packages is not a good idea, because it's up to you to deal with updates. 
Hope that helps.

Cheerio

---

### Post by strabes on 2007-06-06
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by dude1234 on 2007-06-06
Thanks for the helpful replies gents, but I might not have made my _real _issue clear:-

I do not want to download thunderbird again. Nor do I want to look in anyone's repository :-).

I have already downloaded a "thunderbird-2.0.0.0.tar.gz" file over a fast connection, put the files on my memory stick, and later put the file onto the hdd of my ubuntu 6.10 pc. Thousands of people get software this way.

Now I'd just like to install the program.

---

### Post by liveforfunnow on 2007-06-06
> **dude1234 said:**
> Thanks for the helpful replies gents, but I might not have made my _real _issue clear:-

I do not want to download thunderbird again. Nor do I want to look in anyone's repository :-).

I have already downloaded a "thunderbird-2.0.0.0.tar.gz" file over a fast connection, put the files on my memory stick, and later put the file onto the hdd of my ubuntu 6.10 pc. Thousands of people get software this way.

Now I'd just like to install the program.

Thousands of Windows/Mac users, not Ubuntu/Linux users. On Ubuntu, programs are installed in one central location via the APT protocol. An easy graphical frontend, Synaptic, is the central location. As others have mentioned, the easiest and best way to install anything (in Ubuntu Linux) is to open Synaptic (System >> Administration) and type the name of the program. While I am sure another talented forum member can help with the manual install, I have never manually downloaded a program (aside from Automatix) in my 1+ year of using Ubuntu full-time.

---

### Post by screaminj3sus on 2007-06-06
search for thunderbird in synaptic, check box, apply, done

---

### Post by dude1234 on 2007-06-06
Gents, thanks for the help on this. 

Say, that I've put Ubuntu on my mom's computer and I want to install a new program for her. She doesn't have the internet. How would I do this? I won't be able to go to the repository, will I? Is Ubuntu suited to people who don't have the internet?

---

### Post by meman63 on 2007-06-06
Let me get this straight.You downloaded Thunderbird in a .gz format from another box.Transferred 
it to a USB stick,and want to install from the USB stick because of no internet connection there?

If you have no internet connection,why do you need Thunderbird?

Sorry,but just wondering.

Mounting a USB stick is not hard,..But there is an easier way.

It seems to me that if you have a CD of Ubuntu,you should be able to install from there.

Probably easier than building.

Regards,
      Meman63

---

### Post by renzokuken on 2007-06-07
> **dude1234 said:**
> Gents, thanks for the help on this. 

Say, that I've put Ubuntu on my mom's computer and I want to install a new program for her. She doesn't have the internet. How would I do this? I won't be able to go to the repository, will I? Is Ubuntu suited to people who don't have the internet?


you can browse the repos through your browser on any pc. go to [http://archive.ubuntu.com](http://archive.ubuntu.com) (this is where synaptic/apt-get downloads the packages from). find the package you want, it must be the ".deb" file

then to install it run

```
sudo dpkg -i name_of_prog.deb
```

ubuntu is debian based so always try to find a .deb package before using the source (.tar.gz). and if you have an internet connection available, always ALWAYS check Synaptic first

---

### Post by dude1234 on 2007-06-07
Renzokuken - thanks, your answer I can understand.

---

### Post by renzokuken on 2007-06-07
no trubs dude, i remember how confusing it was when i first started using debian based distros. but now i realise how much better it is and cant recommend it enough.

---

### Post by dude1234 on 2007-06-08
Gents

What does it tell you if go to the terminal and I type:- sudo apt-get update.

and the result is that I get a bundle of errors saying "could not connect to ubuntu"?

So then I go to firefox browser and I can happily browse or surf to any internet site I choose.

Another point to be aware of is that I have disabled ipv6 in the alias file and blacklisted it too because that was necessary to get firefox working.

---

### Post by dude1234 on 2007-06-09
following from my previous comment..................

I've re-enabled ipv6 in the blacklist and the aliases files and that didn't help anything.

I've looked at the error message after I use the apt-get command and the server which my apt-get is looking for is "au.archive.ubuntu.com" so i went to my windows pc and entered [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) in the address and there is nothing there. However, if I try [http://archive.ubuntu.com](http://archive.ubuntu.com) then I get a ubuntu repository. (Note how I removed the "au" from the front of the address.)

Does this mean that my version of ubuntu is peculiar? Maybe it was an Australian version? Can I change the location where the apt-get command goes to look for the repository?

Could the problem still be with the ipv6 protocol being used for the apt-get command?

---

### Post by dude1234 on 2007-06-09
The reason why ubuntu wasn't able to find the updates was because it couldn't connect to the internet. Disabling ipv6 didn't help. I had to upgrade the firmware in my D-Link DSL-504T modem and now I have all the functionality of ubuntu software upgrade manager. 

I will still continue investigations into how to upgrade from a previously downloaded file copied onto my HDD. When ubuntu connected to the internet this morning it found 240MB of updates. 240MB is my whole month allocation so I need to do it the other way as I am paying off a house and internet costs are at the bottom of my budget.

---

### Post by Amblonyx on 2007-06-10
Dude
Not much help there he. I just have the same question but from a different point. I run an accounting program in Australian Tax format. This program is Windows based as I have always run a Microsoft OS. I am not happy with Microsoft anymore and like to convert to Linux Ubuntu. Now I found a program called Win4Lin that should allow Windows programs to install and run on Linux computers. I downloaded Win4Lin but how do I install this on the Ubuntu machine?  
Anyone...... Please
A second problem I found is that I can receive emails via Evolution but my password from the ISP does not take on the SMPT site so I can't sent emails
Thanks guys and galls ofcourse
Harry

---

### Post by dude1234 on 2007-06-11
Amblonyx

You should start a separate new post with your issue.

I think you want a dual boot system to run windows programs. The software is, I believe, called WINE but this is the limit of my knowledge.

---

### Post by renzokuken on 2007-06-12
win4lin is an old fork of wine or something.

i would recommend proper wine personally.

its in synaptic or just run

```
sudo apt-get install wine
```

---

### Post by Benoone on 2007-06-28
> **renzokuken said:**
> 
ubuntu is debian based so always try to find a .deb package before using the source (.tar.gz). and if you have an internet connection available, always ALWAYS check Synaptic first

Thanks for being a good teacher :p

Your post solved my problems.

Regards

Benoone

---

### Post by renzokuken on 2007-06-29
glad to be of service, happy ubunting Benoone

---

