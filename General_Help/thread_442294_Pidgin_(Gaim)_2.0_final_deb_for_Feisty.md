---
title: "Pidgin (Gaim) 2.0 final deb for Feisty?"
date: 2007-05-13
forum: General Help
---

### Post by endo on 2007-05-13
Will it be available soon? It's out already. Any info anyone? In the official repositories there's still beta 6 :(
Are they going to update the repos with Pidgin version 2.0 final or are we going to have to wait for Gusty Gibbon?
Or any idea where the 2.0 final .deb can be downloaded from? Any additional repo that has to be included in sources.list?

---

### Post by TopasPV on 2007-05-13
I hope this helps: 
[http://ubuntuforums.org/showthread.php?t=437239](http://ubuntuforums.org/showthread.php?t=437239)

---

### Post by cborga1985 on 2007-05-13
[SIZE="3"]**[COLOR="Red"]If you are inpatient like me use mlind's repo [http://ubuntuforums.org/showpost.php?p=2649312&postcount=7](http://ubuntuforums.org/showpost.php?p=2649312&postcount=7) . He has backported the debs from Gutsy to Feisty and they work quite well.[/COLOR]**[/SIZE]

---

### Post by endo on 2007-05-13
Lots of thanks to both of you, but is there any chance that they will continue to maintain the official repos with future official updates to pidgin regularly?
Or will we always have to update Pidgin like this?

---

### Post by strabes on 2007-05-13
Eventually they'll put Pidgin into the repos.

---

### Post by endo on 2007-05-13
> **strabes said:**
> Eventually they'll put Pidgin into the repos.

I really hope this happens before the release of Gusty :)

---

### Post by mlind on 2007-05-13
I also uploaded gutsy's pidgin for feisty, it's available from
```

deb http://www.telemail.fi/mlind/ubuntu feisty main

```

---

### Post by cborga1985 on 2007-05-14
> **mlind said:**
> I also uploaded gutsy's pidgin for feisty, it's available from
```

deb http://www.telemail.fi/mlind/ubuntu feisty main

```

Is there anything different in the Gutsy Pidgin?

---

### Post by kalpik on 2007-05-14
@everyone: Please have a look here: [http://ubuntuforums.org/showthread.php?p=2647568](http://ubuntuforums.org/showthread.php?p=2647568)

---

### Post by endo on 2007-05-17
It's available at [http://www.getdeb.net/](http://www.getdeb.net/)
I got it from there and it works perfectly fine... at least for now :)

---

### Post by mlind on 2007-05-18
> **cborga1985 said:**
> Is there anything different in the Gutsy Pidgin?

nope. It's just a backport for Feisty. Only change is build-depend against libnss-dev instead of libnss3-dev.

---

### Post by IgnorantGuru on 2007-05-18
I tried to install the gutsy version and got all kinds of dependency version problems.  I'm just going to wait a few days for it to show in the feisty repos.

---

### Post by mlind on 2007-05-18
> **IgnorantGuru said:**
> I tried to install the gutsy version and got all kinds of dependency version problems.  I'm just going to wait a few days for it to show in the feisty repos.

If you want to try gutsy's pidgin for feisty
```

deb http://www.telemail.fi/mlind/ubuntu feisty main

```
To get the public signing key
```

wget http://www.telemail.fi/mlind/ubuntu/937215FF.gpg -O- | **sudo** apt-key add -

```

---

### Post by cborga1985 on 2007-05-18
> **mlind said:**
> If you want to try gutsy's pidgin for feisty
```

http://www.telemail.fi/mlind/ubuntu feisty main

```
To get the public signing key
```

wget http://www.telemail.fi/mlind/ubuntu/937215FF.gpg -O- | apt-key add -

```
Most people probaly know this but you should correct ```
http://www.telemail.fi/mlind/ubuntu feisty main
``` to read ```
deb http://www.telemail.fi/mlind/ubuntu feisty main
``` Not sure if you know but your signing key is not working. The packages worked great and thanks for making them.

---

### Post by zasf on 2007-05-19
> **mlind said:**
> If you want to try gutsy's pidgin for feisty
```

http://www.telemail.fi/mlind/ubuntu feisty main

```
To get the public signing key
```

wget http://www.telemail.fi/mlind/ubuntu/937215FF.gpg -O- | apt-key add -

```

thanks for the repo, pidgin is working great and maintained gaim's stuff.

I also update gaim to your transitional package.. btw what does it mean? Should we remove gaim? 

```
$ dpkg -l | grep gaim
ii  gaim                                       2.0.0+dfsg.1-3ubuntu1~feisty0.1            transitional package to Pidgin
ii  gaim-data                                  2.0.0+beta6-1ubuntu4                       multi-protocol instant messaging client - da

```

Thanks,
Matteo

---

### Post by Princey on 2007-05-19
Can't add the key and apt-get update fails thereof: > wget [http://www.telemail.fi/mlind/ubuntu/937215FF.gpg](http://www.telemail.fi/mlind/ubuntu/937215FF.gpg) -O- | apt-key add -
--06:49:04--  [http://www.telemail.fi/mlind/ubuntu/937215FF.gpg](http://www.telemail.fi/mlind/ubuntu/937215FF.gpg)
           => `-'
Resolving [www.telemail.fi](www.telemail.fi)... 62.240.64.131
Connecting to www.telemail.fi|62.240.64.131|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,076 (2.0K) [text/plain]

100%[====================================>] 2,076         --.--K/s

06:49:05 (75.84 KB/s) - `-' saved [2076/2076]

gpg: no writable keyring found: eof
gpg: error reading `-': general error
gpg: import from `-' failed: general error


> Failed to fetch [http://www.telemail.fi/mlind/ubuntu/dists/feisty/main/binary-amd64/Packages.gz](http://www.telemail.fi/mlind/ubuntu/dists/feisty/main/binary-amd64/Packages.gz)  404 Not Found
Reading package lists... Done
W: GPG error: [http://www.telemail.fi](http://www.telemail.fi) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFFF5E937215FF
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


Running 64bit here, could that be the reason for the 2nd error? Thinking of compiling, but not sure if there'll be additional packages needed.

---

### Post by zasf on 2007-05-19
add

```
**deb** http://www.telemail.fi/mlind/ubuntu feisty main
```

to your sources.list instead of

```
http://www.telemail.fi/mlind/ubuntu feisty main
```

and execute the other command as root

```
sudo -s
wget http://www.telemail.fi/mlind/ubuntu/937215FF.gpg -O- | apt-key add -
```

Matteo

---

### Post by Princey on 2007-05-19
I get past the key problem, but still get the error when I type in > sudo apt-get update

> Failed to fetch [http://www.telemail.fi/mlind/ubuntu/dists/feisty/Release](http://www.telemail.fi/mlind/ubuntu/dists/feisty/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


And yes, I ensured like before that it's > deb [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty main  that's added to my sources.list

---

### Post by cborga1985 on 2007-05-19
> **Princey said:**
> Can't add the key and apt-get update fails thereof: 



Running 64bit here, could that be the reason for the 2nd error? Thinking of compiling, but not sure if there'll be additional packages needed.

it's only a i386 repo but you could add this as a source ```
deb-src http://www.telemail.fi/mlind/ubuntu feisty main
```and then just do```
sudo apt-get update
apt-get source gaim
sudo apt-get build-dep pidgin
sudo apt-get install fakeroot build-essential
cd pidgin*
fakeroot dpkg-buildpackage

```

This is what I used to do allot when I couldn't use a 32 bit repository.

---

### Post by mlind on 2007-05-19
> **cborga1985 said:**
> Most people probaly know this but you should correct ```
http://www.telemail.fi/mlind/ubuntu feisty main
``` to read ```
deb http://www.telemail.fi/mlind/ubuntu feisty main
``` Not sure if you know but your signing key is not working. The packages worked great and thanks for making them.

oops, thanks. Signing key should work, I just forgot to add sudo call before apt-key command.

---

### Post by mlind on 2007-05-19
> **zasf said:**
> 
I also update gaim to your transitional package.. btw what does it mean? Should we remove gaim? 

Thanks,
Matteo

The transitional gaim package is needed to satisfy ubuntu-desktop & friends which still depend on gaim. You can remove gaim-data though.

---

### Post by Princey on 2007-05-19
> **cborga1985 said:**
> it's only a i386 repo but you could add this as a source ```
deb-src http://www.telemail.fi/mlind/ubuntu feisty main
```and then just do```
sudo apt-get update
apt-get source gaim
sudo apt-get build-dep pidgin
sudo apt-get install fakeroot build-essential
cd pidgin*
fakeroot dpkg-buildpackage

```

This is what I used to do allot when I couldn't use a 32 bit repository.

Reached as far as changing to the pidgin directory. Here's the error message: > cd pidgin*
bash: cd: pidgin*: No such file or directory

---

### Post by mlind on 2007-05-19
> **Princey said:**
> Reached as far as changing to the pidgin directory. Here's the error message:

You must be in the parent directory where you executed "apt-get source pidgin" (not apt-get source gaim, you don't want gaim's source package).

---

### Post by zasf on 2007-05-19
> **mlind said:**
> The transitional gaim package is needed to satisfy ubuntu-desktop & friends which still depend on gaim. You can remove gaim-data though.

great, thanks!

---

### Post by Princey on 2007-05-19
Thanks for pointing out the error. I'm still stuck though and wondering if downloading the i386 deb and doing a ```
sudo dpkg -i --force-architecture
``` instead. Will that do it? Error message is as follows: > gpg: [stdin]: clearsign failed: secret key not available
dpkg-genchanges
dpkg-genchanges: not including original source code in upload
dpkg-buildpackage: binary and diff upload (original source NOT included)
(WARNING: Failed to sign .dsc and .changes file)
 then throws me back at the prompt in the pidgin directory.

---

### Post by mlind on 2007-05-19
> **Princey said:**
> Thanks for pointing out the error. I'm still stuck though and wondering if downloading the i386 deb and doing a ```
sudo dpkg -i --force-architecture
``` instead. Will that do it? Error message is as follows:  then throws me back at the prompt in the pidgin directory.

I dunno about --force-architechture option.

If you compile using dpkg-buildpackage, use -us and -uc flags to skip the source package signing part
```

dpkg-buildpackage -rfakeroot -us -uc

```
I suggest to use pbuilder for this instead. Check my sig for HOWTO link.

---

### Post by cborga1985 on 2007-05-19
> **Princey said:**
> Thanks for pointing out the error. I'm still stuck though and wondering if downloading the i386 deb and doing a ```
sudo dpkg -i --force-architecture
``` instead. Will that do it? Error message is as follows:  then throws me back at the prompt in the pidgin directory.


Those particular errors are not important because you are using someone else's sources that were made on their system. If it built then just do this to install it.```
cd ..
sudo dpkg -i *.deb
```

Also, I do not recommend forcing packages to install because it can damage your file system.

---

### Post by Princey on 2007-05-19
> **cborga1985 said:**
> Those particular errors are not important because you are using someone else's sources that were made on their system. If it built then just do this to install it.```
cd ..
sudo dpkg -i *.deb
```

Also, I do not recommend forcing packages to install because it can damage your file system.

Thanks much, that last command did the trick.:popcorn: Installed and running now.:guitar:

---

### Post by cborga1985 on 2007-05-20
> **Princey said:**
> Thanks much, that last command did the trick.:popcorn: Installed and running now.:guitar:

No problem, glad to hear you got it working.:cool:

---

### Post by tehmatticus on 2007-05-20
I'd love to use your repo, mlind, but sadly you have no support for amd64.  Does anyone know of a 64bit pidgin repo?

---

### Post by cborga1985 on 2007-05-20
Princey
Would you mind attaching your debs for other people to use?

---

### Post by Princey on 2007-05-20
> **cborga1985 said:**
> Princey
Would you mind attaching your debs for other people to use?

Sure I would, but there are 4 debs. Which of those or do I attach all of them?

---

### Post by Princey on 2007-05-20
> **tehmatticus said:**
> I'd love to use your repo, mlind, but sadly you have no support for amd64.  Does anyone know of a 64bit pidgin repo?

There are no existing 64 bit debs for now as far as I know. I built mine by myself and have the debs if you're interested. cborga1985 asked me to upload mine for anyone interested. I asked him for clarification. You can get mine if you can't wait. They're a total of about 11MB (4 of them). I can send them via gmail in the meanwhile.

---

### Post by cborga1985 on 2007-05-21
> **Princey said:**
> There are no existing 64 bit debs for now as far as I know. I built mine by myself and hae the debs if you're interested. cborga1985 asked me to upload mine for anyone interested. I asked him for clarification. You can get mine if you can't wait. They're a total of about 11MB (4 of them). I can send them via gmail in the meanwhile.
The forums won't let you just attach debs so you should put all four of them in a archive format such as Gzip(tar.gz) using file-roller.

---

### Post by Princey on 2007-05-21
> **cborga1985 said:**
> The forums won't let you just attach debs so you should put all four of them in a archive format such as Gzip(tar.gz) using file-roller.

Thanks for the info. However, there's a limit too on the size of the gzip file. I might have to find a temporary file hosting space and post the url then. I'll look about tonight and try to have it posted to this thread in the morning before I go off to work.

---

### Post by tehmatticus on 2007-05-22
I found elsewhere that [www.getdeb.net](www.getdeb.net) has 64bit versions, so I grabbed them from there.  I'm still working on getting pidgin-otr working, however.  If anyone's got luck with that, lemme know.

---

### Post by cborga1985 on 2007-05-22
> **tehmatticus said:**
> I found elsewhere that [www.getdeb.net](www.getdeb.net) has 64bit versions, so I grabbed them from there.  I'm still working on getting pidgin-otr working, however.  If anyone's got luck with that, lemme know.

those will work but the packages in mlind's repo make and a smooth transition from Gaim to Pidgin.

---

### Post by tehmatticus on 2007-05-23
Right, which is why I was hoping there were 64bit debs, yet he does not seem to have them on his repository.

---

### Post by Princey on 2007-05-23
[SIZE="3"][FONT="Georgia"]For those interested in native 64bit debs, here's the[ [COLOR="Red"]link[/COLOR]]("http://web.omnidrive.com/APIServer/public/7xeP2mLIfSXWk1dq6fO6lsy6/pidgin2.0.0_amd64.tar.gz") to mine compiled on my x64 machine running Feisty. They're compressed in gzip format so here's the instructions to install.```
tar zxvf pid(tab)
``` followed by ```
cd pid(tab)
```
then ```
sudo dpkg -i *.deb
``` and all should be well.





*Note: (tab) means you press the tab key for autocompletion.[/FONT][/SIZE]

---

### Post by cborga1985 on 2007-05-25
removed

---

### Post by endo on 2007-05-25
Why don't you just get it from [http://getdeb.net](http://getdeb.net) instead of messing with those additional repos?

---

### Post by jusmurph on 2007-05-25
> **Princey said:**
> [SIZE="3"][FONT="Georgia"]For those interested in native 64bit debs, here's the[ [COLOR="Red"]link[/COLOR]]("http://web.omnidrive.com/APIServer/public/7xeP2mLIfSXWk1dq6fO6lsy6/pidgin2.0.0_amd64.tar.gz") to mine compiled on my x64 machine running Feisty. They're compressed in gzip format so here's the instructions to install.```
tar zxvf pid(tab)
``` followed by ```
cd pid(tab)
```
then ```
sudo dpkg -i *.deb
``` and all should be well.
[/FONT][/SIZE]
This is what i get following this guide 
```

Selecting previously deselected package pidgin.
(Reading database ... 100852 files and directories currently installed.)
Unpacking pidgin (from pidgin_2.0.0+dfsg.1-3ubuntu1~feisty0.1_amd64.deb) ...
Replacing files in old package gaim ...
Selecting previously deselected package pidgin-data.
Unpacking pidgin-data (from pidgin-data_2.0.0+dfsg.1-3ubuntu1~feisty0.1_all.deb) ...
Selecting previously deselected package pidgin-dbg.
Unpacking pidgin-dbg (from pidgin-dbg_2.0.0+dfsg.1-3ubuntu1~feisty0.1_amd64.deb) ...
Selecting previously deselected package pidgin-dev.
Unpacking pidgin-dev (from pidgin-dev_2.0.0+dfsg.1-3ubuntu1~feisty0.1_all.deb) ...
dpkg: dependency problems prevent configuration of pidgin:
 pidgin depends on libavahi-compat-howl0 (>= 0.6.0); however:
  Package libavahi-compat-howl0 is not installed.
dpkg: error processing pidgin (--install):
 dependency problems - leaving unconfigured
Setting up pidgin-data (2.0.0+dfsg.1-3ubuntu1~feisty0.1) ...

dpkg: dependency problems prevent configuration of pidgin-dbg:
 pidgin-dbg depends on pidgin (= 1:2.0.0+dfsg.1-3ubuntu1~feisty0.1); however:
  Package pidgin is not configured yet.
dpkg: error processing pidgin-dbg (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pidgin-dev:
 pidgin-dev depends on pidgin (= 1:2.0.0+dfsg.1-3ubuntu1~feisty0.1); however:
  Package pidgin is not configured yet.
 pidgin-dev depends on libgtk2.0-dev; however:
  Package libgtk2.0-dev is not installed.
dpkg: error processing pidgin-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pidgin
 pidgin-dbg
 pidgin-dev
```

---

### Post by mlind on 2007-05-26
@ jusmurph
If you're just missing package dependencies,  "sudo apt-get install -f"  or "sudo aptitude upgrade" should fix this for you

---

### Post by nicweb on 2007-05-27
2.0.1 is available at [http://www.getdeb.net/app.php?name=Pidgin](http://www.getdeb.net/app.php?name=Pidgin)

---

### Post by gizmoarena on 2007-06-19
do i need to remove gaim before installing pigdin? 
i have seen on other threads that it doesn't work if gaim is installed!

can anyone tell me that how can I remove gaim without removing the dependencies.
I guess I only need to remove gaim, and gaim-data to remove GAIM. but if I try to remove them,
it says it will remove 
> nautilus-sendto
ubuntu-desktop


---

### Post by pjalegria on 2007-06-19
Same problem ...:(

---

### Post by Princey on 2007-06-19
> **gizmoarena said:**
> do i need to remove gaim before installing pigdin? 
i have seen on other threads that it doesn't work if gaim is installed!

can anyone tell me that how can I remove gaim without removing the dependencies.
I guess I only need to remove gaim, and gaim-data to remove GAIM. but if I try to remove them,
it says it will remove

No, you don't have to. It needs gaim and the dependencies. Remember, pidgin is gaim renamed.

---

### Post by gizmoarena on 2007-06-20
When I run pigdin, it says I says to install SSL support.

I have libssl, and libssl-dev installed. what else I need to support SSL? :|

---

### Post by jusmurph on 2007-06-20
> **mlind said:**
> @ jusmurph
If you're just missing package dependencies,  "sudo apt-get install -f"  or "sudo aptitude upgrade" should fix this for you

Wow, i forgot i posted here and found a deb at debget.

Anyway, these commands... are these universal, what do they do exactly?
<--- trying to learn rather than c&p

---

### Post by Princey on 2007-06-20
> **jusmurph said:**
> Wow, i forgot i posted here and found a deb at debget.

Anyway, these commands... are these universal, what do they do exactly?
<--- trying to learn rather than c&p

As far as I know, aptitude is an alternative to apt-get that does a more 'cleaner' install of meta packages making it easier to more cleanly remove applications when installed. However, the update command updates your sources list and checks for potention errors.

```
sudo apt-get install -f
``` is used (I believe) to fix errors that may appear especially if packages are broken or dependencies missing. There may be other uses but these two have been those I've had to use that command for. Other useful commands are:

sudo apt-get autoremove - cleans up left over dependencies no longer needed 

sudo apt-get check - checks apt-get to see if everything is in other. There are others, but I can't remember them off hand. I'll put together a list of apt-get commands and what they do sometime later this week if I get the time to.

---

### Post by gizmoarena on 2007-06-21
:| ummm, I asked something ... 
anyone know the answer?

---

