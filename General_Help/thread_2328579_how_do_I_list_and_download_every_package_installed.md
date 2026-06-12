---
title: "how do I list and download every package installed on the system?"
date: 2016-06-22
forum: General Help
---

### Post by a.dusty.trail on 2016-06-22
I wiped my apt cache a while back.
But now I want to get a copy of every package and dependency that is running on the system so I have an off line back up.

I would like every package possible for backup including the core desktop packages in case I have to bring back lubuntu or xubuntu and I only have a Ubuntu install disk.

Thank you for the info
All I've found so far is re install instructions.

---

### Post by QDR06VV9 on 2016-06-22
I can only speak for what I have used and works as advertised...so Aptik is a good tool for such tasks. 
[http://www.howtogeek.com/206454/how-to-backup-and-restore-your-apps-and-ppas-in-ubuntu-using-aptik/](http://www.howtogeek.com/206454/how-to-backup-and-restore-your-apps-and-ppas-in-ubuntu-using-aptik/)

Another Method for backing up Desktop...but I say this loosely because I have no firsthand experience with this Backup Ubuntu Desktop Using sbackup Simple Backup GNOME Tool; 
[http://www.thegeekstuff.com/2011/10/sbackup-for-ubuntu/](http://www.thegeekstuff.com/2011/10/sbackup-for-ubuntu/)

But if you have the extra space Clonezilla will make a .img of your entire system
[http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone)

And if you are not put-off by the Terminal you can use DD (***Used with caution***) to copy bit for bit of your system.
[http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/)
This should give you some good info for making your decision.
Regards

---

### Post by oldfred on 2016-06-22
I prefer to just backup the list of installed apps. Then I do not get into out of sync dependency issues.
But I have high speed Internet so it is easy to download packages.

       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade 
    
If you have used ppa, you need to backup sources as well.
 But do not just import all sources as that can lead to issues of versions:
[http://askubuntu.com/questions/2038/backup-software-sources](http://askubuntu.com/questions/2038/backup-software-sources)
sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, the tip will only reinstall Ubuntu files, 

      
 List of default applications:
Look for manifests for version:
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)
[http://releases.ubuntu.com/xenial/](http://releases.ubuntu.com/xenial/) 
   Then to install that manifest:
dpkg-query -W --showformat='${Package} ${Version}\n' > casper/filesystem.manifest
apt-get install -y $(awk '{print $1}' filesystem.manifest)

---

### Post by a.dusty.trail on 2016-06-22
I just want the packages.
Not to use apt get to reinstall them.
Or to back up my desktop settings.
Aptik seems to to not back up the core files.

Wget might be a way but I have not found how get it to download the a list of packages.

A simple command script I can run from time to time is what I'm looking to build.
From old install
dpkg --get-selections > ~/my-packages

Is a start but how to have wget or whatever download these packages next to a directory is where I'm at.

---

### Post by &amp;KyT$0P# on 2016-06-22
"download"?  Why not use dpkg-repack?

---

### Post by QDR06VV9 on 2016-06-22
> **halogen2 said:**
> "download"?  Why not use dpkg-repack?
That is also a good method...but perhaps some Information should have been linked.
[https://debian-administration.org/article/499/Re-creating_Debian_binary_packages_with_dpkg-repack](https://debian-administration.org/article/499/Re-creating_Debian_binary_packages_with_dpkg-repack)

---

### Post by a.dusty.trail on 2016-06-22
Will the repacked packages be exact in every way as downloading them?

I would have thought the originals would be easier to download with high speed internet than to repackage and if necessary check against the repository mirror for tampering or changes if necessary..

At least that is the theory I was using.
(I see that dpkg repack will use the current configuration files from host not the originals, that might cause problems)

---

### Post by &amp;KyT$0P# on 2016-06-22
> Will the repacked packages be exact in every way as downloading them?
Not necessarily.  From the man page:
```
DESCRIPTION
       dpkg-repack creates a .deb file  out  of  a  Debian  package  that  has
       already been installed on your system.

       If any changes have been made to the package while it was unpacked (ie,
       conffiles files in /etc modified), the new  package  will  inherit  the
       changes. (There are exceptions to this, including changes to configura&#8208;
       tion files that are not conffiles, including those managed by ucf.)

       This utility can make it easy to copy packages  from  one  computer  to
       another, or to recreate packages that are installed on your system, but
       no longer available elsewhere.

       Note: dpkg-repack will place the created package in the current  direc&#8208;
       tory.

```

> (I see that dpkg repack will use the current configuration files from host not the originals, that might cause problems)
:confused:
What configuration file changes are you making that might cause problems if repacked into a .deb file?

---

### Post by a.dusty.trail on 2016-06-22
I would prefer the originals.
I do tend to mess with things fron time to time. Rarely tracking the changes as they are usually a whim and not a requirement.

Originals would just be safer I think.

There must be a way to just download then all simply.

---

### Post by ajgreeny on 2016-06-22
Just a thought using synaptic if you find it easier with a GUI and you really must do what you've asked for.

First install **synaptic** and open it and click **Reload**.
Go to the **Status** tab in left pane and click **Installed** which will list everything on your machine that came from enabled repos.
Click in the top package then scroll to bottom, hold shift and click on the bottom package to select the whole list.
Go to **Package** menu and choose **Reinstall**.  It will take a while to setup the reinstall process.
Click the Apply button and in the window that appears click in the "**Download package files only**"
Lastly click in the Apply bottom in that window and all packages will be downloaded to /var/cache/apt/archives but not reinstalled.

You can see in my screenshot that it may be a large download of thousands of packages, but it should do it for you.

---

### Post by a.dusty.trail on 2016-06-22
> **ajgreeny said:**
> Just a thought using synaptic if you find it easier with a GUI and you really must do what you've asked for.

First install **synaptic** and open it and click **Reload**.
Go to the **Status** tab in left pane and click **Installed** which will list everything on your machine that came from enabled repos.
Click in the top package then scroll to bottom, hold shift and click on the bottom package to select the whole list.
Go to **Package** menu and choose **Reinstall**.  It will take a while to setup the reinstall process.
Click the Apply button and in the window that appears click in the "**Download package files only**"
Lastly click in the Apply bottom in that window and all packages will be downloaded to /var/cache/apt/archives but not reinstalled.

You can see in my screenshot that it may be a large download of thousands of packages, but it should do it for you.
Thank you im giving it a try as i speak....

so far it has hung with 50% processor being used.
for about 10 minutes so far   2474 applications installed..

ill wait and see if it come back at all or if it just choked on the workload...
of marking the packages to be reinstalled 

if anyone has a command line method of doing this.. 
it just feels nicer seeing that something is happening...

---

### Post by a.dusty.trail on 2016-06-23
right now im testing this method
dpkg --get-selections > ~/my-packages
cat my-packages | xargs sudo apt-get download

but it fails if anything is wrong at all
and i would like it to ignore any errors ( but prefeabley list them)
and download

addding the  -n 1 argument to xargs makes each command on one line and errors just  are errored
and it goes to the next and you do need sudo so that can be skipped .

dpkg --get-selections > ~/my-packages
cat my-packages | xargs -n 1 apt-get download

so all that is left is finding out how to set the directory you want to download to

then setting it all in one line or makeing a script to run

---

### Post by QDR06VV9 on 2016-06-23
> **a.dusty.trail said:**
> 

if anyone has a command line method of doing this.. 
it just feels nicer seeing that something is happening...
This will not do it any quicker but as you requested a command to do the same.
The following command in the terminal grabs the list of installed packages and downloads, [U][B]packages will be stored at /var/cache/apt/archives
[/B][/U]
```
dpkg -l | grep "^ii"| awk ' {print $2} ' | xargs sudo apt-get -y --force-yes install --reinstall --download-only
```

---

### Post by ajgreeny on 2016-06-23
> **runrickus said:**
> This will not do it any quicker but as you requested a command to do the same.
The following command in the terminal grabs the list of installed packages and downloads, [U][B]packages will be stored at /var/cache/apt/archives
[/B][/U]
```
dpkg -l | grep "^ii"| awk ' {print $2} ' | xargs sudo apt-get -y --force-yes install --reinstall --download-only
```
Nice one runrickus!

Does exactly what I showed using synaptic but using cli.

---

### Post by QDR06VV9 on 2016-06-23
> **ajgreeny said:**
> Nice one runrickus!

Does exactly what I showed using synaptic but using cli.

Well Thank You ajgreeny:)
Took me a bit to figure out...but it needed the flag "--download-only"

---

