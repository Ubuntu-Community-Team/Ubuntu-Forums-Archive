---
title: "Installation of Firefox on (K)Ubuntu 5.04"
date: 2005-07-13
forum: General Help
---

### Post by oldcodger on 2005-07-13
I have downloaded Firefox (firefox-1.0.43.tar.gz) from Mozilla.org, unzipped it and moved it to my /usr/local/apps directory. I do not know how to proceed from there.
The installation instructions on the Mozilla website say;

'cd firefox-installer
./firefox-installer'

but this will not work for me as this is not the 'installer' version.

Further, ./[filename] doesn't seem to work for me on Kubuntu.

I picked up a snatch of: 'A Tutorial: How To Install Firefox in Linux', but despite exhaustive 'Googling'. cannot find the whole tutorial.

Can anyone help. please?

Thanks

old codger

---

### Post by codejunkie on 2005-07-13
you can easily install the newest version of firefox avaliable for ubuntu/kubuntu by adding the backports repos to your /etc/apt/sources.list file by folowing this guide [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) and doing sudo apt-get install firefox at the terminal or through synaptic. or you can manually install the one from firefox.com the easiest way is to download the installer, place it in your home dir because you have full permissions to install software here, extracting it and then run the installer by double clicking the firefox-installer and choosing run. you may be running into troubles because you don't have permissions to install files in the /usr dir. if you wan't manually install firefox systemwide you have to create a folder in /usr that you have permission to access for example: /usr/firefox like this  ```
sudo mkdir /usr/firefox
``` then give yourself permission to install files to it like this ```
sudo chmod 777 /usr/firefox -R
``` then run the installer and choose the dir /usr/firefox as your install location hope this helps.

---

### Post by oldcodger on 2005-07-16
Thanks, codejunkie. What a palaver - and I'm no nearer installing Firefox than before! Please don't misunderstand me, I'm not criticising your attempt to help - just the crazy system and the fact that Ubunutu doesn't include Firefox, or make it easy to install.

[quote]
you can easily install the newest version of firefox avaliable for ubuntu/kubuntu by adding the backports repos to your /etc/apt/sources.list file by folowing this guide [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) and doing sudo apt-get install firefox at the terminal [unquote]

First, this is what happened:
[code]
fred@ubuntu:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
Password:
fred@ubuntu:~$ sudo gedit /etc/apt/sources.list
sudo: gedit: command not found
[code]

 - which was a good start! 'sudo: gedit: command not found'[!]

So I pressed on, found the /etc/apt/sources.list, modified it as instructed and saved it. Did the two 'gpg' commands OK, but when I tried 'sudo apt-get update',
I got about 35 lines of text, starting with:

'Get:1 http://gb.archive.ubuntu.com hoary Release.gpg [189B]
Get:2 http://gb.archive.ubuntu.com hoary-updates Release.gpg [189B]
Get:3 http://security.ubuntu.com hoary-security Release.gpg [189B]
...'

down to:

'Get:9 ftp://ftp.nerim.net testing/main Packages [18.9kB]
Fetched 74.1kB in 1s (39.6kB/s)
Failed to fetch ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz  MD5Sum mismatch
Failed to fetch ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-i386/Packages.gz  MD5Sum mismatch
Reading package lists... Done
W: Couldn't stat source package list ftp://ftp.nerim.net stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.nerim.net testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.'

I thought that: 'You may want to run apt-get update to correct these problems' was a bit rich!

Undeterred, I tried: 

[code]
fred@ubuntu:~/downloads$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list ftp://ftp.nerim.net stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.nerim.net testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package firefox
fred@ubuntu:~/downloads$
[code]
 
Again: 'You may want to run apt-get update to correct these problems'[!]

So I again tried: 

[code]
fred@ubuntu:~/downloads$ sudo apt-get update
[code]

with the same result as before - except that this time I got: 

[code]
'Failed to fetch ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz  MD5Sum mismatch []code]...etc, etc, after: 

[code]
Get:7 ftp://ftp.nerim.net testing/main Packages [18.9kB]
[code]

[quote]
the easiest way is to download the installer, place it in your home dir because you have full permissions to install software here, extracting it and then run the installer by double clicking the firefox-installer and choosing run.
[unquote]

So I did. The only problem was that, when I double-clicked 'firefox-installer', it just opened - no sign of a 'run' option!

All in all, I feel thoroughly frustrated and confused - am I being made fun of?

What have I done wrong?

Any help you can give would be much appreciated.

Thanks

Best
old codger

---

### Post by angkor on 2005-07-16
I didn't fully read the entire thread, so forgive me if this doesn't make sense, but why don't you just install firefox through apt?

sudo apt-get install mozilla-firefox

Or use the graphical frontend synaptic...

---

### Post by fannymites on 2005-07-16
I've just installed firefox 1.0.5 via the firefox-installer but it seems to be having an identity crisis.
If I type "about:" in the url bar it says 1.0.5 in big blue letters but the user agent string below it shows Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.7.9) Gecko/20050711 Firefox/1.0.4
It's the same under Help>About Mozilla-Firefox.
So which version is it? and how do I get it to show up right?

---

### Post by codejunkie on 2005-07-16
[QUOTE=oldcodger]Thanks, codejunkie. What a palaver - and I'm no nearer installing Firefox than before! Please don't misunderstand me, I'm not criticising your attempt to help - just the crazy system and the fact that Ubunutu doesn't include Firefox, or make it easy to install.
[/QUOTE]

[I]first firefox is include with ubuntu and kubuntu it is the default web browser for both versions so you should already have it installed unless you did a custom install and chose not to install it or something went wrong. second i was not trying to mislead you or as you put it 
> **palaver**Talk intended to beguile or deceive i was trying to answer your question because i wanted to help, and i was just telling you some of the different ways to do what you asked.[/I]

The reason your getting the error about gedit: command not found is your using kde as your desktop enviorment not gnome. **the guides at ubuntuguide are based on gnome commands** but can be applied to kde, sorry i should have told you this at the time but i didn't think of it my bad. so ***gedit*** is just the text editor for gnome. so since your using kde you have to use the text editor for kde which is ***kate*** so you would use this ```
sudo kate /etc/apt/sources.list
``` insted of ```
sudo gedit /etc/apt/sources.list
``` the reason your getting this error
```
W: Couldn't stat source package list ftp://ftp.nerim.net stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
```
those are not official ubuntu/kubuntu reposotories and they could just be down your /etc/apt/sources.list file should look like this 
```

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
``` so run ```
sudo kate /etc/apt/sources.list
``` remove everything listed there except the top line which is your kubuntu cd [SIZE=4]*do not remove that*[/SIZE] and copy and paste the above repos to your /etc/apt/sources.list file save the file and close kate then run ```
sudo apt-get update
``` and then ```
sudo apt-get install firefox
```hope this helps.

---

### Post by oldcodger on 2005-07-17
Thanks, codejunkie.

All due to a misunderstanding - and a difference in definition. My Concise Oxford Dictionary says:

'**palaver** *n* . **1**  fuss and bother, esp. prolonged.'

> first firefox is include with ubuntu and kubuntu it is the default web browser for both versions so you should already have it installed unless you did a custom install and chose not to install it or something went wrong.

Then 'something must have gone wrong' because I installed the 'default' version from the CD - and searched for it and it wasn't there.

Anyway, by a series of accidents and lucky breaks - and a tip from angkor -  have this morning installed Firefox.

It was so early in the morning (about 5.30 BST) that I can't remember precisely how I did it, but it involved yet another 

```
sudo apt-get update
``` and a 

```
sudo apt-get install mozilla-firefox
``` (thanks, angkor), and there it was - well nearly! 

Thanks also for the other interesting info you gave which I shall save for future reference.

And thanks again for your help.

As the great man said: 'All's well that ends well' [!]

Best

old codger

---

### Post by oldcodger on 2005-07-17
[QUOTE=angkor]
sudo apt-get install mozilla-firefox
.[/QUOTE]

Thanks, angkor.

I finally managed it this morning.

Thanks again.

Best

old codger :grin:

---

### Post by codejunkie on 2005-07-17
Glad you got it working, sorry if i made it rougher for you than it had to be to get it working that really wasn't my intention.

---

### Post by angkor on 2005-07-17
[QUOTE=oldcodger]Thanks, angkor.

I finally managed it this morning.

Thanks again.

Best

old codger :grin:[/QUOTE]

You're welcome...:) 

The only reason to install firefox from the mozilla site is if you _really_ want to have the latest version 1.05 (if it comes with a really nice new feature or something).  Ubuntu does not upgrade the version but implements all the security updates / fixes that come with the newer versions through the Ubuntu update manager.

---

