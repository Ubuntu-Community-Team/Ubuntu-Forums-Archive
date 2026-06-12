---
title: "apt-fast : A Bash Script to Speed Things Along"
date: 2008-06-04
forum: General Help
---

### Post by ilikenwf on 2008-06-04
**[SIZE="3"]12/22/2011: [/SIZE]I've moved development of apt-fast to github. **Note that the current version I have not tested yet, so I need testers...and users...and people to improve apt-fast and put in pull requests :)

**[SIZE="4"][https://github.com/ilikenwf/apt-fast]("https://github.com/ilikenwf/apt-fast")[/SIZE]**

I wrote this script that combines the power of the axel download manager with the stability of apt-get. All you have to do is make sure axel is installed from the repos, or from [here]("http://alioth.debian.org/frs/?group_id=100070"), and then put this script somewhere, name it apt-fast, and chmod +x on it. Then, call it like you would apt-get or aptitude, just by sudo ./apt-fast dist-upgrade, or whatever it is you want to install or do.

If you have any improvements to this puppy, please share them so I can share them from [my website]("http://www.mattparnell.com/projects/apt-fast-and-axel-roughly-26x-faster-apt-get-installations-and-upgrades.html"). Right now, I don't have many variables set, so you can only install single packages one or two at a time. I believe an array would be a good fix for that, but I don't have time right now. A further improvement would be the addition of auto complete, like apt-get has, so that you don't have to type entire package names. Whatever the case, enjoy, and don't use this too often, as it really rapes the package servers.

---

### Post by bainssu on 2010-05-19
:popcorn:Nice script,

I have added a check to restrict undesired calling of axel when a non existing package is entered.

i.e.

apt-fast install foobar



```
#!/bin/sh
#apt-fast by Matt Parnell [http://www.mattparnell.com](http://www.mattparnell.com) , this thing is FOSS
#please feel free to suggest improvments to [EMAIL="admin@mattparnell.com"]admin@mattparnell.com[/EMAIL]
# Use this just like apt-get for faster package downloading. Make sure to have axel installed

#If the first user entered variable string contains apt-get, and the second string entered is either install or dist-upgrade
if echo "$1" | grep -q "[upgrade]" || echo "$2" | grep -q "[install]" || echo "$2" | grep -q "[dist-upgrade]"; then
  echo "Working...";

  #Go into the directory apt-get normally puts downloaded packages
  cd /var/cache/apt/archives/;

  #Have apt-get print the information, including the URI's to the packages
  apt-get -y --print-uris $1 $2 $3 $4 > debs.list;

  #Strip out the URI's, and download the packages with Axel for speediness
  # check to ensure we return http/ftp addresses

        egrep -o -e "(ht|f)tp://[^\']+" debs.list

        if [ $? = "0" ] ; then
                 egrep -o -e "(ht|f)tp://[^\']+" debs.list | xargs -l1 axel -a;

        fi

  #Perform the user's reqested action via apt-get
  apt-get -y $1 $2 $3 $4;

  echo "Done! Make sure and check to see that the packages all were installed properly. If a package is erred, run sudo apt-get autoclean and try installing it again without the use of this script.";

elif echo "$1" | grep -q "
[*]"; then
  apt-get $1;
else
  echo "Sorry, but you appear to be entering invalid options. You must use apt-get and one of apt-get's options in order to use this script.";
fi

```

---

### Post by TaTaE on 2010-08-28
This could be easily implemented in Ubuntu.

Also one day, we can discover the wheel. Maybe.

---

### Post by ilikenwf on 2010-08-28
> **TaTaE said:**
> This could be easily implemented in Ubuntu.

Also one day, we can discover the wheel. Maybe.

I use Archlinux now, but I updated the script...

There are some modded versions that work with aria2c there too...contributed by users...PCLinuxOS people and Ubuntu users both have been making it even better...even with autocompletion.

[http://www.mattparnell.com/projects/apt-fast-and-axel-roughly-26x-faster-apt-get-installations-and-upgrades.html](http://www.mattparnell.com/projects/apt-fast-and-axel-roughly-26x-faster-apt-get-installations-and-upgrades.html)

---

### Post by amgmagician on 2011-04-11
I made some modification. Here the final code:
```
#!/bin/sh
# apt-fast by Matt Parnell http://www.mattparnell.com
# Modified by Ali Ghaffaari
# This thing is FOSS. Please feel free to suggest improvments to admin@mattparnell.com
# Use this just like apt-get for faster package downloading. Make sure to have axel installed

# Check for root permission
if [ "$USER" != "root" ]; then
	echo You are not root. Permission denied!
	exit 1
fi

# Filter 'install', 'upgrade' and 'dist-upgrade' options
if [ "$1" = "upgrade" ] || [ "$1" = "install" ] || [ "$1" = "dist-upgrade" ]; then
	echo "\033[01m[apt-fast] Working ...\033[0m";

	# Go into the directory apt-get normally puts downloaded packages (partial section)
	cd /var/cache/apt/archives/partial;

	# Have apt-get print the information, including the URI's to the packages
	apt-get -y --print-uris $* > debs.list;

	# Strip out the URI's, and download the packages with Axel for speediness
	# Check to ensure we return http/ftp addresses

	egrep -o -e "(ht|f)tp://[^\']+" debs.list > /dev/null 2>&1

	if [ $? = "0" ] ; then
		# Downloading the packages
		head -n $(( `cat debs.list|wc -l` - `egrep -o -e "(ht|f)tp://[^\']+" debs.list|wc -l` )) debs.list
		echo -n "Do you want to continue [Y/n]? "
		read ANS;
		if [ -z $ANS ] || [ "$ANS" = "Y" ] || [ "$ANS" = "y" ]; then
			echo do nothing > /dev/null
		else
			echo "\033[01m[apt-fast] Abort\033[0m"
			exit 0
		fi

		echo "\033[01m[apt-fast] Downloading packages ...\033[0m"
		egrep -o -e "(ht|f)tp://[^\']+" debs.list | xargs -l1 axel -a;
		echo

		# Moving downloaded packages to parent directory
		mv *.deb .. > /dev/null 2>&1
	fi

	# Perform the user's reqested action via apt-get
	echo "\033[01m[apt-fast] Installing packages ...\033[0m"
	apt-get -y $*;

	# Check the apt-get exit code
	if [ $? = "0" ]; then
		echo "\033[01m[apt-fast] Done!\033[0m";
	else
		echo "\033[01m[apt-fast] Failed!\033[0m";
		exit $?
	fi

# Pass other options to original apt-get!
else
	apt-get $*;
fi

```

---

### Post by ilikenwf on 2011-04-11
> **amgmagician said:**
> I made some modification. Here the final code:
...



Without having to trace through, care to tell us what it is you did to make it better?

---

### Post by amgmagician on 2011-04-12
> **ilikenwf said:**
> Without having to trace through, care to tell us what it is you did to make it better?

Yes, you're right! I was sleepy last night! :D
First of all, specially thanks for your nice work.
I used your apt-fast script and found that some modifications [maybe] make it better:
1- 'root' checking was added at the first of the script.
2- In the main IF-ELSE structure, 'upgrade', 'install' and 'dist-upgrade' options are filtered and the other options are passed to 'apt-get' itself. Obviously, wrong options are detected by 'apt-get' itself.
Annotation: I think for example 'grep [install]' filters the text which have the letters 'i', 'n', 's' and etc separately. For example '**in**duc**t**' is accepted with [install] filter which is not acceptable for our goal. I tested it and it works as I say. Am I mistaken?
3- Some text formatting was added. I made the outputs of 'apt-fast' bold to be distinguishable from 'apt-get' and 'axel' outputs and I also added '[apt-fast]' label at the first of its output.
4- In new script downloading process are done in '/var/cache/apt/archive/partial/' rather than '/var/cache/apt/archive'. When download finish successfully, downloaded packages are moved to '/var/cache/apt/archive'. It's exactly what 'apt-get' does.
5- When we install a package with 'apt-get'. It prints some information about packages which are going to download and install and ask us "Do you want to continue [Y/n]?". I added this functionality to the script too. First, I print the information which had been inserted to debs.list file without showing urls with this command:
```
head -n $(( `cat debs.list|wc -l` - `egrep -o -e "(ht|f)tp://[^\']+" debs.list|wc -l` )) debs.list
```
and then ask the user "Do you want to continue [Y/n]?". If the answer is yes, it starts to download the packages.

That's it. :)
In addition, I forgot to remove the line 'Modified by ...'. Sorry, I added this comment to specify that it's different from previous 'apt-fast' which I had downloaded.

Sincerely,
Ali

---

### Post by ilikenwf on 2011-04-12
> **amgmagician said:**
> Yes, you're right! I was sleepy last night! :D
First of all, specially thanks for your nice work.
I used your apt-fast script and found that some modifications [maybe] make it better:
1- 'root' checking was added at the first of the script.
2- In the main IF-ELSE structure, 'upgrade', 'install' and 'dist-upgrade' options are filtered and the other options are passed to 'apt-get' itself. Obviously, wrong options are detected by 'apt-get' itself.
Annotation: I think for example 'grep [install]' filters the text which have the letters 'i', 'n', 's' and etc separately. For example '**in**duc**t**' is accepted with [install] filter which is not acceptable for our goal. I tested it and it works as I say. Am I mistaken?
3- Some text formatting was added. I made the outputs of 'apt-fast' bold to be distinguishable from 'apt-get' and 'axel' outputs and I also added '[apt-fast]' label at the first of its output.
4- In new script downloading process are done in '/var/cache/apt/archive/partial/' rather than '/var/cache/apt/archive'. When download finish successfully, downloaded packages are moved to '/var/cache/apt/archive'. It's exactly what 'apt-get' does.
5- When we install a package with 'apt-get'. It prints some information about packages which are going to download and install and ask us "Do you want to continue [Y/n]?". I added this functionality to the script too. First, I print the information which had been inserted to debs.list file without showing urls with this command:
```
head -n $(( `cat debs.list|wc -l` - `egrep -o -e "(ht|f)tp://[^\']+" debs.list|wc -l` )) debs.list
```
and then ask the user "Do you want to continue [Y/n]?". If the answer is yes, it starts to download the packages.

That's it. :)
In addition, I forgot to remove the line 'Modified by ...'. Sorry, I added this comment to specify that it's different from previous 'apt-fast' which I had downloaded.

Sincerely,
Ali

Nice! Are you the same guy that emailed me?

I really need to set this up on github or launchpad...

---

### Post by amgmagician on 2011-04-14
No, I'm not that guy! :)

---

### Post by ilikenwf on 2011-12-22
12/22/2011: I've moved development of apt-fast to github. Note that the current version I have not tested yet, so I need testers...and users...and people to improve apt-fast and put in pull requests

[https://github.com/ilikenwf/apt-fast](https://github.com/ilikenwf/apt-fast)

Just bumping to alert you all.

---

### Post by r1ft on 2012-04-30
Has anyone managed to get this working in 12.04?

---

### Post by amgmagician on 2012-05-03
> **r1ft said:**
> Has anyone managed to get this working in 12.04?

It's a simple script but a little messy. I'm trying to fix some bugs and write a clean, generic, and flexible script.
In addition, I'm going to build a package for apt-fast and share it ASAP. ;) It can be run on almost all debian-based systems.

---

### Post by sportfreak2020 on 2012-05-03
testing this today in 12.04 server installation .. will update back!

---

### Post by vasa1 on 2012-05-03
> **r1ft said:**
> Has anyone managed to get this working in 12.04?
Works just fine.

---

### Post by sportfreak2020 on 2012-05-03
it works !

---

### Post by strobon on 2012-05-11
manage to install it on 12.04,works fine so far.
but 2 problem:
1.seems like the auto completion doesn't working for me
```
cp ./apt-fast.comp /etc/bash_completion.d/apt-fast
. /etc/bash_completion
```
run this command,check the folder,everything is in order.but not work.

2.this is silly question,but how to complete replace the apt-get with apt-fast? so ubuntu software center use it too.
i try rename apt-get to aptg.get.old and link apt-fast to apt-get,but its not working for me.


:lolflag:for my bad english.
pardon me..

---

### Post by vasa1 on 2012-06-26
[http://iloveubuntu.net/apt-fast-164-released-fixes-and-proper-configuration-dialog](http://iloveubuntu.net/apt-fast-164-released-fixes-and-proper-configuration-dialog)

But [this page]("https://github.com/ilikenwf/apt-fast") doesn't have any mention of 1.6.4 ???

But the launchpad page refers to the git page so my doubts have vanished.

But there's no mention of a ppa as yet on the Launchpad page ([https://launchpad.net/apt-fast](https://launchpad.net/apt-fast)). Back to being confused.

---

### Post by vasa1 on 2012-06-26
Okay, the ppa is here: [https://launchpad.net/~apt-fast](https://launchpad.net/~apt-fast)

---

### Post by vasa1 on 2012-06-30
I noticed one difference from the earlier version. I'm not sure it's because of a tweak I made or didn't make. Either way ...

In **Configuration options** (/etc/apt-fast.conf), ensure that "DOWNLOADBEFORE=true" is _not_ commented out. If it is commented out and you don't pay attention, you may be timed out and then there's a chance that you may need to download ~ 6 MB of data again (because of the [large updates in 12.04]("https://bugs.launchpad.net/launchpad/+bug/1001780")). 

```
# Enable DOWNLOADBEFORE to suppress apt-fast confirmation dialog and download
# packages directly.
#
# Default: dialog enabled
#
DOWNLOADBEFORE=true
```

---

### Post by vasa1 on 2012-10-08
Apt-fast gets a mention again: [http://www.webupd8.org/2012/10/speed-up-apt-get-downloads-with-apt.html](http://www.webupd8.org/2012/10/speed-up-apt-get-downloads-with-apt.html)

---

### Post by ilikenwf on 2012-11-28
Glad everyone likes it! While I've moved away from using Ubuntu a long time ago, I still try and maintain the script and manage pull requests when I can...I do still use Debian for my servers, though.

That said, I must admit that [Lasall/Dominique Lasserre]("https://github.com/Lasall") is doing the majority of improvements and git management nowadays...he's doing a great job, and this script is still quite handy.

I read somewhere that apt supposedly can do multiple threads on downloads, but apt-fast's real benefit is using aria to allow downloading each thread from a different mirror...

---

