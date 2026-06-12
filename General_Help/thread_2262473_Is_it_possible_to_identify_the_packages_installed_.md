---
title: "Is it possible to identify the packages installed using &quot;apt-get install&quot; command?"
date: 2015-01-25
forum: General Help
---

### Post by arroy_0209 on 2015-01-25
In my desktop running Ubuntu 12.04 I had installed several programs using sudo apt-get install command. Now I have installed lubuntu in a laptop in which some of those programs should be installed (e.g., gimp, xfig, latex, c++ compiler). Is it possible to identify the packages installed and copy to the laptop using pendrive and manually install the required programs? Please indicate how this can be done.

---

### Post by Holger_Gehrke on 2015-01-25
The package manager keeps log files in '/var/log/apt/history*'.  The older logs are gzip compressed, the log files are rotated, only the last twelve are kept with '/var/log/apt/history.12.gz' being the oldest. 

The command
```

(zcat /var/log/apt/history.log.{12,11,10,9,8,7,6,5,4,3,2,1}.gz; cat /var/log/apt/history.log)|grep -B 1 'Install:'

```
concatenates the logs, searches for installations and prints the command used for installation and the list of installed packages.

---

### Post by ibjsb4 on 2015-01-25
Maybe dpkg-repack would work for you.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dpkg-repack&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dpkg-repack&sa=Search&cof=FORID:9)

---

### Post by deadflowr on 2015-01-25
If you run
```
dpkg --get-selections >> packages.txt
```
It'll make a text file(called packages.txt) in your home folder, which will list ALL packages currently installed on your system.

You can then reverse this and install these packages, as a whole, with
```
sudo dpkg --set-selections < package.txt
sudo apt-get -u dselect-upgrade
```

.
You can also reinstall directly from a custom file, which is actually really simple,
Make a file and list one package per line, something like
```
gimp
audacity
vlc

```
and any other files you want and save it as a txt file.
Then run apt-get install like so,
```
sudo apt-get install $(cat my-saved.txt)
```
and apt-get will read through the txt file and begin installing whatever packages are listed.

I personally find the second method easier, as adding packages to a text file is quite simple.
(And I tend to install packages willy-nilly and quite a few would have no real need to be re-installed, which is troublesome to remove from the get-selections method, but no trouble with the $(cat file.txt)
method.

On another note, the Ubuntu Software Center can also show you all installed packages, go to Installed.
(Though the software center is nowhere near as fast...) 


Also, these ,method require a network connection.
If what you ask is if it is possible to transfer the packages without an internet connection, it is, sort of.
(And I'm on the fence about recommending it)

When you install a package from Ubuntu's repositories if downloads a debian package.
That debian packages gets stored in a folder in /var/cache/apt/archives.
If you never run the command
```
sudo apt-get clean
```
you would have all those install packages, or else it would be emptied by that command.
So if you wanted to try and install from those packages, you could copy them into a personal folder and to reinstall you could run
```
cd folder-where-I-stored-those-deb-packages
sudo dpkg -i *.deb
```


I do not know how helpful any of this may be, but there it is...

---

### Post by NM5TF on 2015-01-25
@DeadFlower...

thanx for these really great time saving tips....

learned something new today....

---

