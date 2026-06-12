---
title: "install plugins for rhythmbox"
date: 2017-05-09
forum: General Help
---

### Post by hilario_ferreira on 2017-05-09
Hi all:

I'm trying to install some plugins for rhythmbox (ILirics, equalizer etc...) but  so far I didn't succed.
I followed this instructions : [http://ubuntuhandbook.org/index.php/2014/07/install-rhythmbox-plugins-ubuntu-1404/](http://ubuntuhandbook.org/index.php/2014/07/install-rhythmbox-plugins-ubuntu-1404/)

But it's not working.

After following those instruction I go to : home/myname/local/share/rhythmbox and ther's only : playlists.xml   - podcast-timestamp  and rhythmdb.xml . no plugins installed.

can someone please tell how to do this ??

---

### Post by #&amp;thj^% on 2017-05-09
First did you open rhythmbox then go to and go to Tools -> Plugins. Enable plugins you want from the list.
Also give the return here from the terminal:
```
apt policy rhythmbox-plugin-llyrics
```

---

### Post by hilario_ferreira on 2017-05-09
Hi 1fallen

I see no where in my rhythmbox the menu : tools !!!!

entering the code :
apt policy rhythmbox-plugin-llyrics  gives the following return: invalid operation policy

---

### Post by #&amp;thj^% on 2017-05-09
> **hilario_ferreira said:**
> Hi 1fallen

I see no where in my rhythmbox the menu : tools !!!!

entering the code :
apt policy rhythmbox-plugin-llyrics  gives the following return: invalid operation policy

Ok on the right hand side you will see a gear by the volume (icon of a speaker) Click that and scroll to plugins,
Now you should see the plugins options for you choose from...if installed that is.
See my Screenshot

---

### Post by howefield on 2017-05-09
> **hilario_ferreira said:**
> I followed this instructions : [http://ubuntuhandbook.org/index.php/2014/07/install-rhythmbox-plugins-ubuntu-1404/](http://ubuntuhandbook.org/index.php/2014/07/install-rhythmbox-plugins-ubuntu-1404/)

That tutorial won't work for many currently supported versions of Ubuntu, ie anything later than 16.04. If the advice from 1fallen doesn't get you going please post the version of Ubuntu that you are using.

---

### Post by #&amp;thj^% on 2017-05-09
> **howefield said:**
> That tutorial won't work for many currently supported versions of Ubuntu, ie anything later than 16.04. If the advice from 1fallen doesn't get you going please post the version of Ubuntu that you are using.

He should be ok..

---

### Post by hilario_ferreira on 2017-05-09
> **1fallen said:**
> Ok on the right hand side you will see a gear by the volume (icon of a speaker) Click that and scroll to plugins,
Now you should see the plugins options for you choose from...if installed that is.
See my Screenshot

I'm sorry but I don't have that gear !!! how is that possible ???

---

### Post by howefield on 2017-05-09
> **1fallen said:**
> He should be ok..

And.. ?

The package the tutorial calls for is not available in later repository versions.. nontheless I'm sure the poster will be ok in your hands.

---

### Post by #&amp;thj^% on 2017-05-09
Lets see what you are using for a DE:...open terminal and run this,
```
echo $DESKTOP_SESSION && lsb_release -a
```
paste back the return so we can have a look.

---

### Post by hilario_ferreira on 2017-05-09
> **1fallen said:**
> Lets see what you are using for a DE:...open terminal and run this,
```
echo $DESKTOP_SESSION && lsb_release -a
```
paste back the return so we can have a look.

here it is:

ubuntu
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

---

### Post by #&amp;thj^% on 2017-05-09
> **howefield said:**
> And.. ?

The package the tutorial calls for is not available in later repository versions.. nontheless I'm sure the poster will be ok in your hands.

Ok :D i finally got the ppa was not the same as i was looking at,,,now on the same page.:KS

@hilario_ferreira we need to add this to your instructions...and to get the plugins installed.
This will add the PPA
```
sudo add-apt-repository ppa:fossfreedom/rhythmbox-plugins
```
Now update/refresh your PM with:
```
sudo apt update
```
Now if no errors are shown...>> install the needed plugins again

---

### Post by deadflowr on 2017-05-09
For the record, apt policy was implemented later on.
To run the equivalent on 14.04 use apt-cache policy.
Several apt commands did not exist yet. (like apt autoremove)

Just a little something to keep in the back pocket.

---

### Post by #&amp;thj^% on 2017-05-09
> **hilario_ferreira said:**
> I'm sorry but I don't have that gear !!! how is that possible ???

With Unity the menu will be in the top panel...push your mouse to the top panel with rhythmbox shown in the fore-front, 


> Just a little something to keep in the back pocket.
Thanks I just noticed the 14.04 so good heads up deadflowr.:)

---

### Post by hilario_ferreira on 2017-05-09
> **1fallen said:**
> Ok :D i finally got the ppa was not the same as i was looking at,,,now on the same page.:KS

@hilario_ferreira we need to add this to your instructions...and to get the plugins installed.
This will add the PPA
```
sudo add-apt-repository ppa:fossfreedom/rhythmbox-plugins
```
Now update/refresh your PM with:
```
sudo apt update
```
Now if no errors are shown...>> install the needed plugins again

This is done but I don't see any change.

> **1fallen said:**
> With Unity the menu will be in the top panel...push your mouse to the top panel with rhythmbox shown in the fore-front, 



Thanks I just noticed the 14.04 so good heads up deadflowr.:)

I don't see what you mean !!! "push mouse to the top panel" ?? can you ne more specific please ?? sorry i'm new to ubuntu and i'm not very techy

---

### Post by deadflowr on 2017-05-09
Top panel means top of screen panel.
Unity uses a unique menu system that runs all app menus on the top panel.
But it's hidden until you hover the mouse over the panel.

It only shows for the currently in-focused app.
(if that helps/makes sense)

---

### Post by hilario_ferreira on 2017-05-09
Top panel means top of screen panel.
Unity uses a unique menu system that runs all app menus on the top panel.
But it's hidden until you hover the mouse over the panel.

It only shows for the currently in-focused app.
(if that helps/makes sense)                 



I see.It's ok now.

But this is really weird I would never find it.

Ok thanks to all of you for yr kind assistance

---

