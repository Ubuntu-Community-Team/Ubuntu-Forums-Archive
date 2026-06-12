---
title: "Question about 'add-apt-repository' command"
date: 2016-03-25
forum: General Help
---

### Post by lakeshore2985 on 2016-03-25
Here is a simple question about the "*add-apt-repository*" command.

So I was trying to install Oracle's VirtualBox the correct way and when tried to add repositories for the software, I suddenly ran into questions; for example the official site says to add the line '*deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) trusty contrib*' into the "/etc/apt/sources.list" file. Why can't I do this via terminal? Or what is the correct command for this? I successfully managed to add the line via GUI or Nano'ing the "sources.list" file, but not via terminal. It's kind of confusing since most of other repository entries I have on my machine has instead a "ppa:" naming scheme, not "http://xxx.xxx.xxx" etc.

---

### Post by grahammechanical on 2016-03-25
Did you try using add-apt-repository? There is a man (manual) page for this command as there is for all commands.

```
man add-apt-repository
```

> add-apt-repository is a script which adds an external APT repository to either /etc/apt/sources.list or a file in /etc/apt/sources.list.d/ or removes an already existing repository.

Regards.

---

### Post by lakeshore2985 on 2016-03-25
Yes I did use "*add-apt-repository* man. As I said it's not working for the line in question.

Console outputs the following error:

```
Error: need a single repository as argument
```

---

### Post by qyot27 on 2016-03-25
add-apt-repository *can* be used for traditional 'deb address section' repositories, almost as-is.

For instance, I prefer using the latest [official builds of mkvtoolnix](https://mkvtoolnix.download/downloads.html#ubuntu) instead of the ones in the Ubuntu repositories.  The info is given as the traditional 'add this to your sources.list' as:
(for 15.10):
```
deb http://mkvtoolnix.download/ubuntu/wily/ ./
deb-src http://mkvtoolnix.download/ubuntu/wily/ ./ 
```

But I'd prefer to do it with add-apt-repository so I don't have to worry about opening a text editor.
```
sudo add-apt-repository "deb http://mkvtoolnix.download/ubuntu/wily/ ./"
wget -q -O - https://mkvtoolnix.download/gpg-pub-moritzbunkus.txt | sudo apt-key add -
```
(that second one is just importing the signing keys; not all repos will require that kind of thing)

You have to remember to enclose the entire deb line in double-quotes as the argument to add-apt-repository.

---

### Post by lakeshore2985 on 2016-03-25
> **qyot27 said:**
> add-apt-repository *can* be used for traditional 'deb address section' repositories, almost as-is.

For instance, I prefer using the latest [official builds of mkvtoolnix]("https://mkvtoolnix.download/downloads.html#ubuntu") instead of the ones in the Ubuntu repositories.  The info is given as the traditional 'add this to your sources.list' as:
(for 15.10):
```
deb http://mkvtoolnix.download/ubuntu/wily/ ./
deb-src http://mkvtoolnix.download/ubuntu/wily/ ./ 
```

But I'd prefer to do it with add-apt-repository so I don't have to worry about opening a text editor.
```
sudo add-apt-repository "deb http://mkvtoolnix.download/ubuntu/wily/ ./"
wget -q -O - https://mkvtoolnix.download/gpg-pub-moritzbunkus.txt | sudo apt-key add -
```
(that second one is just importing the signing keys; not all repos will require that kind of thing)

You have to remember to enclose the entire deb line in double-quotes as the argument to add-apt-repository.

Thanks, it worked! Now let me try and understand why.

So basically what is a "PPA" and why do I need to include the symmetric double quotes if the line to be added does not come with PPA? What is the difference between a "PPA" and a "non-PPA" repository address? Also, what is the difference between adding or not that second line "deb-src" from your example? Is that the repository address for the source code or something?

---

### Post by qyot27 on 2016-03-26
> **lakeshore2985 said:**
> So basically what is a "PPA" and why do I need to include the symmetric double quotes if the line to be added does not come with PPA? What is the difference between a "PPA" and a "non-PPA" repository address? Also, what is the difference between adding or not that second line "deb-src" from your example? Is that the repository address for the source code or something?
Technically, any external repository is a 'PPA'.  All 'PPA' stands for is 'Personal Package Archive'...i.e., a plain old repository.  The double quotes are needed because there are space characters in the information, and the double-quotes let add-apt-repository see it as a single item rather than three or more (the word deb, the address, and one or more sections).  The ppa: protocol used on Launchpad doesn't contain spaces, so it can be interpreted as a single item regardless of double-quotes.

The reason that you can go on Launchpad, look up PPAs, and use the ppa: protocol to add them via add-apt-repository is because it translates Launchpad's ppa: address data into the right lines/configuration files to add to the sources.list (or said another way, if you use 'ppa:' it knows to go to Launchpad and grab the data from that shorthand).  There's nothing all that special about it, except that Launchpad is a centralized hosting service and the ppa: protocol they provide also imports the authentication keys along with the rest of the repo data.  If you notice, Launchpad provides a traditional 'copy this to your sources.list and use this GPG key to authenticate it' information box in the write-up for each PPA, so you could do it manually if you wanted.

And yes, the deb-src repo is a repository for the source code of the packages in the deb repo.

---

### Post by lakeshore2985 on 2016-03-26
> **qyot27 said:**
> Technically, any external repository is a 'PPA'.  All 'PPA' stands for is 'Personal Package Archive'...i.e., a plain old repository.  The double quotes are needed because there are space characters in the information, and the double-quotes let add-apt-repository see it as a single item rather than three or more (the word deb, the address, and one or more sections).  The ppa: protocol used on Launchpad doesn't contain spaces, so it can be interpreted as a single item regardless of double-quotes.

The reason that you can go on Launchpad, look up PPAs, and use the ppa: protocol to add them via add-apt-repository is because it translates Launchpad's ppa: address data into the right lines/configuration files to add to the sources.list (or said another way, if you use 'ppa:' it knows to go to Launchpad and grab the data from that shorthand).  There's nothing all that special about it, except that Launchpad is a centralized hosting service and the ppa: protocol they provide also imports the authentication keys along with the rest of the repo data.  If you notice, Launchpad provides a traditional 'copy this to your sources.list and use this GPG key to authenticate it' information box in the write-up for each PPA, so you could do it manually if you wanted.

And yes, the deb-src repo is a repository for the source code of the packages in the deb repo.

Thank you for clearing this up!

---

### Post by oldos2er on 2016-03-27
If your question has been answered to your satisfaction, please mark the thread 'Solved' under the Thread Tools menu at the top of the page. This will help others who may have the same question. Thanks.

---

### Post by lakeshore2985 on 2016-03-27
done!

---

