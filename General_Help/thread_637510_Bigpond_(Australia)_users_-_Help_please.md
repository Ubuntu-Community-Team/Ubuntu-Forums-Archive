---
title: "Bigpond (Australia) users - Help please"
date: 2007-12-11
forum: General Help
---

### Post by jeffbilling on 2007-12-11
I am using 'Bigpond ADSL Service' everything works fine but I CANNOT view any ot their videos - they tell me it is optimised for Internet Explorer 6 or above - can anyone help.

---

### Post by luckykar on 2007-12-11
> **jeffbilling said:**
> I am using 'Bigpond ADSL Service' everything works fine but I CANNOT view any ot their videos - they tell me it is optimised for Internet Explorer 6 or above - can anyone help.

You could try using  the firefox plugin "user agent switcher" its tricks web site's to think your using a different browser , set it to internet explorer 7 and see how you go...

Just another thing make sure you have the correct media codecs installed.

:)

[https://addons.mozilla.org/en-US/firefox/addon/59]("https://addons.mozilla.org/en-US/firefox/addon/59")

---

### Post by jeffbilling on 2007-12-11
Thanks for this - 
I have installed 'User Agent Switcher' and set to Internet Exp 7.
Some progress - I don't get the error message but I still don't get any video.
So I guess it must be the codec.
Which one is it please?
I am still a little confused with all the different Codecs.
:)

---

### Post by luckykar on 2007-12-13
To get codecs working I install these packages : 

w32codecs ubuntu-restricted-extras flashplugin-nonfree libdvdcss2 

You need to have the medibuntu repo installed if you dont  you will need to add it to your sources.list

here is how to do it:

Just copy paste these commands into a terminal.

1. sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

2. wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

Once you have it setup just run the following.

3. sudo  apt-get install w32codecs ubuntu-restricted-extras flashplugin-nonfree libdvdcss2 

you should now be able to watch your video's...:)

If you cant  watch them, install this as well :

sudo apt-get install mplayer mozilla-mplayer

sudo apt-get remove totem-mozilla

hope it helps...

EDIT : If your using Feisty just change the gutsy to feisty in the 1st command

---

### Post by jeffbilling on 2008-01-19
Thanks for this - sorry for delay in replying but have been away for Christmas break.
I have followed the steps but still not getting video.
Things have changed though!!
I now get two messages in the video screen.
1. buffering http//bigpond........
2.connecting to serverbigpondvideo.com ...
These keep alternating quickly between each other and I can't copy them to give exact readout.

---

