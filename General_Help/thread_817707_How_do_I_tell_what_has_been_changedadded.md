---
title: "How do I tell what has been changed/added ?"
date: 2008-06-03
forum: General Help
---

### Post by oygle on 2008-06-03
I'm currently using Gutsy, and wanted to do a reformat and a completely fresh install of Hardy.

Is there any method to determine what has been changed and added in Gutsy, so that I can apply the same changes to Hardy, after it has been installed ?

I did make 2 mods for the grub boot, those are documented, and so will be easy to implement. However, there were a number of new applications added, and I'm 95% sure there were mods done to the Samba side of things, to get networking going with Windows. There was something with printing also.

There must be some easy command like ...

>list_all_the_mods_and_addtions

Oygle

---

### Post by Sam Lars on 2008-06-03
[http://www.ubuntu.com/testing/804rc](http://www.ubuntu.com/testing/804rc)
That's the page for the RC of Hardy, but it's pretty much the same as far as the features go in Hardy.

---

### Post by oygle on 2008-06-03
I already have the Hardy ISO, I just need to know please, is there a method to determine what has been changed/added on Gutsy _before_ I wipe the hard drive ?

---

### Post by Sam Lars on 2008-06-04
I'm sure someone could write a script to do that, comparing everything on the drive to a standard install.

In general, though, unless you edited configuration files in /etc or somewhere like that, your home directory is the only thing that would need to be backed up.  You can install all of the programs again.

---

### Post by oygle on 2008-06-05
Okay thanks. Yes, the home directory wasn't very big. I think there were some files in /etc that had been changed, settings for the network side of things. It wasn't too big, I may as well back that up as well.

---

### Post by zvacet on 2008-06-05
If you want to install same packages in Hardy which you had in Gutsy

```
dpkg --get-selections > installed-software
```

this command will make text file in your home directory.Mail it to yourself (I believe that you have yahoo,gmail... account) and after installing Hardy download it to your home directory.To install same packages again

```
dpkg --set-selections < installed-software
```

```
dselect
```

---

### Post by oygle on 2008-06-05
Thanks, is there meant to be something after the "dselect" command ??

I have found some examples at [Clone Your Ubuntu installation -- Debian Admin]("http://www.debianadmin.com/clone-your-ubuntu-installation.html")

---

### Post by oygle on 2008-06-20
The methods above describe what _packages_ have been installed, and how to re-install them after Hardy.

How do I tell what configuration changes have been made ?  Are they all to be found in the one path ?

For example, I modified

System  |  Admin  |  Network

then searched for the file. It was found in /etc/hosts

Are all configuration changes in the /etc path , are are they in other paths as well ? (**edit**: Just found [this thread]("http://ubuntuforums.org/showthread.php?t=834161&highlight=backup") , and it is recommended to backup /var/lib as well ).

Is there such a tool/command in Ubuntu, to backup all the user configurations and settings ?

Oygle

---

### Post by oygle on 2008-06-24
How do I tell what configuration changes have been made ? Are they all to be found in the one path ?

---

### Post by Sam Lars on 2008-06-29
In /etc, you can find all of the generic config files, and in /etc/programname, you can find config for certain programs.  If you haven't changed them, though, then you shouldn't have to back them up.

---

### Post by oygle on 2008-06-30
Thanks Sam.  :)

It might be a slight overkill, but I've installed sBackup and will backup these paths ..

/etc
/home
/usr
/var

I think that will surely get all the user config/settings files.

Thanks,

Oygle

---

