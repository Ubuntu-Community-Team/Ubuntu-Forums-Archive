---
title: "adobe flash player"
date: 2008-05-02
forum: General Help
---

### Post by notesetter on 2008-05-02
Hello.

I'm having some trouble installing the Adobe Flash plug-in for Firefox in Ubuntu-Studio 8.04. I follow the instructions on the Adobe website, but I get an error message when I try to enter the installation path:

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/mozilla

WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): 
david@ubuntudavid:~/Desktop$ 

Do I have the installation path wrong? A quick search in terminal reveals that /usr/lib/mozilla is a location in my file system. But is this not the installation path for Firefox?

Any help is much appreciated.

Thanks,

Dave

I don't recall having this problem under Gutsy. Might this be a bug?

---

### Post by Aearenda on 2008-05-02
I think it is /usr/lib/firefox in Hardy.

---

### Post by Zorael on 2008-05-02
/usr/lib/mozilla is the shared folder for all Mozilla browsers, and that *is* where you want your Flash installed.

Doesn't the flash-nonfree package do the trick?

---

### Post by atomkarinca on 2008-05-02
This is probably easier: open up a terminal and type:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Aearenda on 2008-05-02
Interesting - I had the same problem as notesetter and so chose /usr/lib/firefox - but now I see that the PDF plugin is installed in /usr/lib/mozilla - very confusing! I think I will try uninstalling the existing flash plugin and do it again as atomkarinca suggests. IIRC this wasn't available at the point in the alpha cycle when I installed originally.

---

### Post by notesetter on 2008-05-02
That does the trick. Thanks. I wonder how many other plugins and programs I've manually installed that would have been easier using apt-get...

---

### Post by Nepherte on 2008-05-02
Most plugins have a corresponding package in the repositories:
[list][*]movie players like mplayer, totem, vlc, ...
[*]adobe acrobat (medibuntu repo)
[*]flash player
[*]java
[*]...[/list]

---

### Post by atomkarinca on 2008-05-02
> **notesetter said:**
> That does the trick. Thanks. I wonder how many other plugins and programs I've manually installed that would have been easier using apt-get...

codecs:

```
sudo apt-get install ubuntu-restricted-extras
```

java:

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

dvd codec:

```
sudo apt-get install libdvdcss2
```

---

### Post by Zmrlzna on 2008-05-02
Hi everybody,

first of all let me tell that I'm using Ubuntu since half a year so I have not much experience with Linux; this forum is being very useful and wants to thanks all the people answering questions in here but finally the time I couldn't find an answer has arrive and because of that here is my first question.

I've installed the Adobe Flash Player but Firefox is still using the GNU Flash and cannot find any way to change that. Somebody can help me?

Thank you very much,

Roger

---

### Post by Zorael on 2008-05-02
Hum. Try entering this in a terminal.
```
$ sudo update-alternatives --config mozilla-flashplugin
```
And this as well, I guess.
```
$ sudo update-alternatives --config firefox-flashplugin
```

I only have one option myself, but perhaps you have several.

---

### Post by atomkarinca on 2008-05-02
> **Zmrlzna said:**
> Hi everybody,

first of all let me tell that I'm using Ubuntu since half a year so I have not much experience with Linux; this forum is being very useful and wants to thanks all the people answering questions in here but finally the time I couldn't find an answer has arrive and because of that here is my first question.

I've installed the Adobe Flash Player but Firefox is still using the GNU Flash and cannot find any way to change that. Somebody can help me?

Thank you very much,

Roger

By GNU Flash if you mean Gnash, then I guess first you should remove it. System > Administration > Synaptic Package Manager, then search gnash, click on it and select "mark for complete removel" then search for flashplugin-nonfree and select "mark for installation" and hit apply. That should do the trick.

---

### Post by Zmrlzna on 2008-05-02
I've deleted the Gnash and reinstalled the Flash Player, still not working and now I cannot open any web page in flash!! Crazy, some idea??

---

