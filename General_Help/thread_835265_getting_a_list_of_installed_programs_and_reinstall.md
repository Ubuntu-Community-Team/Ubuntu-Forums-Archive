---
title: "getting a list of installed programs and reinstalling"
date: 2008-06-20
forum: General Help
---

### Post by dexter.deepak on 2008-06-20
i am on ubuntu (hardy)
i want to make a local repository of the installed programs (there are a lot of them !!)...but since i have had a shortage of disk space , i often used apt-get clean.
now  the only way to make a repo is to redownload the packages. 

so i want a script that gets a list of all installed programs and reinstalls them...which will automatically serve my purpose of downloading all of the stuff.

---

### Post by drs305 on 2008-06-20
This command will create a file with all the currently installed packages:
```
sudo dpkg --get-selections >~/Desktop/installed-pkgs

```

This will restore all the packages in the list:
```
sudo dpkg --clear-selections
dpkg --set-selections <~/Desktop/installed-pkgs
sudo apt-get dselect-upgrade 

```

---

### Post by dexter.deepak on 2008-06-20
this method did generate the list but it didnt seem to reinstall/redownload the stuff needed (it was too quick !!)
so my actual purpose of getting the packages in the /var/cache/apt/archives/ remains unsolved yet !

---

### Post by drs305 on 2008-06-20
When I read you were short of disk space I didnt' realize you wanted to actually download all the debs for your currently installed packages. You are correct that the above process was too quick for what you want - it was quick because the apps are already installed on your computer. It didn't need to download anything because you essentially told it to make sure that everything listed a few minutes ago is installed right now. Sorry for my confusion.

What you want is APT-on-CD:

[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")

It has the added advantage of not taking up your valuable empty disk space.

---

### Post by ajgreeny on 2008-06-20
But just installing aptoncd will still not download anything, will it.  You need to see what you have installed using apt (apt-get, synaptic, aptitude or add-remove).  I'm sure there must be a way to find this in terminal with a simple command, but if so, I can't remember nor can I find the log files or whatever will show this.

So open up a  spreadsheet and synaptic, and in synaptic go to File>>History.  A dialog will open up with all the dates of your system updates and program installs and by using that you can copy all the programs to the spreadsheet.

Now comes the worst bit as you will need to delete all the duplicates (ie, different versions) and just leave the package names.  As you have used a spreadsheet this is quite easy as when you copy you can make sure the copy dialog notes spaces as the separator.  This puts the package names into the first column, and by sorting this you can get rid of all duplicates.  You will end up with a long list of all the packages installed with synaptic etc.  You can then download but not unpack or install all the packages with ```
sudo apt-get install -d long list of package names all separated with a space
```I know this is long winded, but it will do the job as far as I can see.  I just hope someone knows a more simple method using the command line.

---

### Post by drs305 on 2008-06-20
> **ajgreeny said:**
> But just installing aptoncd will still not download anything, will it.  

From the APT-on-CD web site, the capabilities seem to include an option to download all the installed debs, which I believe is what the OP wants.

---

### Post by ajgreeny on 2008-06-20
> **drs305 said:**
> From the APT-on-CD web site, the capabilities seem to include an option to download all the installed debs, which I believe is what the OP wants.
Are you certain about that?  I've just looked on the site and can see nothing about that.  Perhaps I've just missed something, but I would be glad if you could point me (and the OP), in the right direction with a web address.  Thanks.

---

### Post by drs305 on 2008-06-20
> **ajgreeny said:**
> Are you certain about that?  I've just looked on the site and can see nothing about that.  Perhaps I've just missed something, but I would be glad if you could point me (and the OP), in the right direction with a web address.  Thanks.

Well, I'm just going to have to download it and see if it can be done. I'll report back.

ADDED:

According to the APTonCD man page:
```


OPTIONS
APTonCD accept the following command-line call methods:
  -c, --packages-list=FILE
   Starts aptoncd listing the packages in FILE

```

I had hoped to be able to import the list generated as I detailed in my first post, combined with aptoncd's -c / --packages-list=FILE switch should allow the desired effect. However, when I run the command an error message is generated stating that the -c switch is not an option. Either the app has been modified since the man page was created or I haven't discerned the correct way to write the command.

In retrospect, the installed-pkgs file generated with the dpkg command is a simple text file that does not have specific version/deb information contained. I suppose it was too much to expect that aptoncd would be able to gather sufficient information to be able to create a download list from such a basic file. Still don't know why it won't accept any kind of "-c" switch... :-(

---

### Post by ajgreeny on 2008-06-20
But even if that worked it would surely need the aptoncd-20080619-CD1.iso file to be successful.  I've also just tried several variations on that command and got nowhere as well, so I remain convinced that aptoncd needs the files already in /var/cache/apt/archives to do anything useful, and as the OP doesn't have anything there aptoncd will not be useful to him at the moment.

Great utility, however, even though the one in hardy doesn't work for restoring from iso at the moment.  There is another updated version which does, however, work proprely [here]("http://www.cypherbios.org/aptoncd/packages/aptoncd_0.1.98-1ubuntu1/binary/aptoncd_0.1.98-1ubuntu1_all.deb").  I use it a lot as I manage my wife's machine and my own and it saves a _lot_ of downloading.

---

