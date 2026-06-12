---
title: "List user installed software"
date: 2020-08-25
forum: General Help
---

### Post by nought2 on 2020-08-25
When preparing to migrate from one OS installation to another I print lists of installed packages.
These can be saved to text files to reference when installing software to a new OS.
In the newly installed OS software items can then be ticked off a list.

Commands like...
snap list
flatpak list
...do these respective parts of the job neatly.

For packages installed via apt I don't know how this might be done.
Sure, I can search packages...
apt list --installed | grep package_name
...but that will only pull up packages one at a time. 
And it provides no reminder of installed packages that do not spring to mind.

I am particularly interested in finding a way to print a list of packages that appear in Show Applications.
They are usually the ones I care about the most. 
Is there any way of creating a list of them?

---

### Post by HermanAB on 2020-08-25
You can simply list all installed packages and run that list on a new machine.  Packages that are already installed will be skipped.

---

### Post by cg-152 on 2020-08-25
The applications that show up in GNOME's "Show Applications" menu all have .desktop files in /usr/share/applications or ~/.local/share/applications.[FONT=inherit]

[/FONT]```
dpkg --search '*.desktop' | awk '{print $1}' | sed "s/://" | sort --unique
```

[FONT=inherit]would list all of their package names, including pre-installed programs.

[/FONT]Source: [https://askubuntu.com/questions/1091235/how-to-get-the-list-of-all-application-installed-which-has-gui](https://askubuntu.com/questions/1091235/how-to-get-the-list-of-all-application-installed-which-has-gui)

---

### Post by nought2 on 2020-08-26
> **cg-152 said:**
> The applications that show up in GNOME's "Show Applications" menu all have .desktop files in /usr/share/applications or ~/.local/share/applications.[FONT=inherit]

[/FONT]```
dpkg --search '*.desktop' | awk '{print $1}' | sed "s/://" | sort --unique
```

[FONT=inherit]would list all of their package names, including pre-installed programs.
[/FONT]Thank you. This produces a list that is close enough to what I was looking for.
The output includes results that are of no interest but I think all the ones I *am* interested in are there too.
> **HermanAB said:**
> You can simply list all installed packages and  run that list on a new machine.  Packages that are already installed  will be skipped.That's very interesting. 
How is it done? Do you have a link to a page where the method is described?

---

### Post by Holger_Gehrke on 2020-08-26
```
apt-mark showmanual
```
 produces a list of all installed packages that have been recorded as 'manually installed'. This list also includes everything installed during the original installation of Ubuntu (the installer sets that attribute so removing some pre-installed software won't break the system). Removing those packages from that list can be done, provided you still have the logs the installer left behind in /var/log/installer. There should be a file /var/log/installer/initial-status.gz. This contains a gzipped detailed list of the packages installed. You can reduce that to a simple list of packages with 
```
sudo zcat /var/log/installer/initial-status.gz | sed -n '/^Package: / s/^Package: //p'
```
The 'sudo' is necessary because the log-file is only accessible for root. Combine the two lists into one , sort it and write out just the packages which are in the list only once
```

(apt-mark showmanual;sudo zcat /var/log/installer/initial-status.gz | sed -n '/^Package: / s/^Package: //p')|sort|uniq -u > ~/packages.list

```
You should now have a text file named packages.list in your $HOME with all manually installed packages but without the ones from the original installation. Using that list to install those packages should be as simple as 'xargs -a packages.list sudo apt install'

Holger

---

### Post by oldfred on 2020-08-26
If upgrading, you may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade
#IF you get this error:
dpkg: warning: package not in database
sudo apt-get install dselect
sudo dselect 
   -> Update
   -> Install

---

### Post by HermanAB on 2020-08-26
Ayup, with this kind of thing, it pays to read the dpkg and apt man pages...

---

### Post by nought2 on 2020-08-26
Yesterday I installed 20.04.1 Focal to a new partition on my boot drive.
After the install I ran...
sudo apt update
sudo apt upgrade
...to get the system up to date. 
Then I added packages to my preference. One at a time from listed notes recorded from a recent good 18.04.5 Bionic installation.

I tested Holger's commands on the new Focal install.

> **Holger_Gehrke said:**
> ```
apt-mark showmanual
```
This produced an output with 68 lines. It's easy for me to see the things I've added there.

I checked /var/log/installer.```
zen@gnuzen:~$ cd /var/log/installer
zen@gnuzen:/var/log/installer$ ls
casper.log  initial-status.gz  partman  telemetry
debug       media-info         syslog   version
```
Log file is still there.
I tried your suggested command:```
(apt-mark showmanual;sudo zcat /var/log/installer/initial-status.gz | sed -n '/^Package: / s/^Package: //p')|sort|uniq -u > ~/packages.list
```Its output file packages.list had 1552 lines. It contained many items that I had not added. But who knows what was updated right after the vanilla install. That update downloaded about 150MB.

To test your suggested install command  'xargs -a packages.list sudo apt install' I would need to create a new install of Focal. Not impossible, but I don't want to do it right at the moment.
> **oldfred said:**
> If upgrading, you may want to edit it to remove  obsolete, old kernels or others. It will not re-install anything already  installed.
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade
#IF you get this error:
dpkg: warning: package not in database
sudo apt-get install dselect
sudo dselect 
   -> Update
   -> InstallAs a test I ran...```
zen@gnuzen:~$ dpkg --get-selections > /media/zen/DG-1gb/dpkg-selections-dg
```
...which saved output to a USB stick. Output has 1882 lines, so ~300 more than Holger's command output.

This looks like a reliable method. I will certainly try it out.
Thanks for posting it, oldfred. If the process works cleanly it will save lots of time.

Thank you all for your responses. 
Although I'm yet to test your suggestions my query has been comprehensively addressed. 
Hence marked solved. 

Cheers,
nought2

---

### Post by oldfred on 2020-08-27
I might compare the two files to see differences.
I have found old kernels and some software I did not want anymore in list, so just manually delete that line. It is just a text file.

---

### Post by nought2 on 2020-08-27
> **oldfred said:**
> I might compare the two files to see differences.
With >1500 lines in each text file it is difficult to compare them manually.

Can that sorting be done via terminal?

Anyhow, in this instance the files were produced from same OS only minutes apart. 
The different commands must be finding different things.

Agreed, a human visual scan would be worthwhile. 
As long as the human knew the type of things to look out for.

---

### Post by mastablasta on 2020-08-27
you can use CLI or GUI based *diff *software. that's what it's called. 

diff is also a command in terminal to compare the two.

just a list off the net so you see what is out there:
[LIST]
[*]diff Command.
[*]Vimdiff Command. ...
[*]Kompare. ...
[*]DiffMerge. ...
[*]Meld – Diff Tool. ...
[*]Diffuse – GUI Diff Tool. ...
[*]XXdiff – Diff and Merge Tool. ...
[*]KDiff3 – – Diff and Merge Tool.
[/LIST]

KDE uses Kompare on desktop for example.

---

### Post by nought2 on 2020-08-28
In my usual affairs I am not often stumped when presented with logic problems and I like to think that my skills in critical thinking are better than the average bear. However, the logic of computing is regularly conceptually baffling. This has especially been the case since I began using Ubuntu. Unix-like computing is taking my noodle to places it has never been before.

I looked into diff. Found instructive articles aimed at teaching how to use the command, how to interpret its output. Even the kindergarten level examples presented for demonstration did not entirely make sense. But I went ahead and had a try.

Earlier in the thread commands provided by oldfred and Holger_Gehrke produced two output files.

fred.txt   (1882 lines)
holger.txt (1552 lines)

The column of package names in fred.txt was accompanied by another column with the only the word 'install' beside each package name. To prevent complications I removed all mentions of the word install. Then I did a few diff experiments.
```

cp fred.txt fred2.txt
sed -i 's/install/ /g' fred2.txt
```
Then I explored various diff options:-```

diff -e holger.txt fred2.txt > H2F.txt
diff -e fred2.txt holger.txt > F2H.txt
diff -y holger.txt fred2.txt > yH2F.txt
diff -y fred2.txt holger.txt > yF2H.txt
diff -u holger.txt fred2.txt > uH2F.txt
diff -u fred2.txt holger.txt > uF2H.txt

```
I struggled to make sense of the output of any of these tests.

After that I checked out options for comparison in GUI. 
Out of:
[LIST]
[*]DiffMerge 
[*]Meld &#8211; Diff Tool 
[*]Diffuse &#8211; GUI Diff Tool 
[*]XXdiff &#8211; Diff and Merge Tool 
[*]KDiff3 &#8211; Diff and Merge Tool 
[/LIST]
...only Meld and KDiff3 could be installed to Ubuntu 20.04.
KDiff3 installed with a number of issues including its show-stopping failure to recognise .txt files.

Which left Meld. Like me, Meld grumbled about the size of the lists it was asked to compare.
The colourised GUI outputs displayed in Meld were still not easy for me to interpret but I did make some headway.

The larger output of Fred's command had more detail. It picked up a couple of items installed as Snaps which would not be installed via repos because they are not available there. In other instances it seemed to be more thorough. For example, qpdfview (a pdf viewer installed by me) was listed once in Holger's output but Fred's found additional plugins installed as well. Holger's output had one grub related listing; Fred's output had seven.

Regarding an automated software install to a new system my session of testing with diff and Meld has led me to conclude I should just suck it and see. Do separate test installs using the methods described by oldfred and Holger_Gehrke and judge by the results. If as oldfred commented packages already installed will not be installed again the process shouldn't become wayward.

---

### Post by TheFu on 2020-08-28
**sdiff** is helpful in wide terminals. It is side-by-side diff. Easier for humans to understand.

Unix has text processing for files as a very strong capability that non-unix people never learned.

The trick to many text comparison solutions is to have only unique lines, sorted files, and identical spacing BEFORE comparisons.
**meld** is pretty great.

---

### Post by nought2 on 2020-08-28
> **TheFu said:**
> **sdiff** is helpful in wide terminals. It is side-by-side diff. Easier for humans to understand.
Thanks. It was easier to read than any of the diff outputs created.
In another thread you suggested OP try **geany** and to launch it via sudoedit. I like it.

> **TheFu said:**
> Unix has text processing for files as a very strong capability that non-unix people never learned.
Oh yeah, its powerful alright. Every little way in which text and system operations can be manipulated has been carved up into seemingly innocuous commands each of which can be manipulated by permitted arguments. It's a massive matrix of possibility.  

Previously using MS Win I never found a way to get started with DOS command. Never really had a need to.
It is not like that with Linux. Users have to dive in straight away. 
It's mostly been good for me so far. Baby steps and small ambitions.
Really do appreciated the help here though.

---

### Post by TheFu on 2020-08-29
> **nought2 said:**
>  
Previously using MS Win I never found a way to get started with DOS command. Never really had a need to. 

That's because MSFT locked up all the configuration in DBs and called it "better."  Foolish people.  Gnome is doing that same crap now.  The farther away from text that things are allowed, the worse it is for software freedom.

Text is better than
html is better than
rtf is better than
pdf is better than
DB is better than 
docx is better than
privately encrypted config files that aren't open to all.

Text is the most universal format and should be the default whenever possible.

IMHO.

---

