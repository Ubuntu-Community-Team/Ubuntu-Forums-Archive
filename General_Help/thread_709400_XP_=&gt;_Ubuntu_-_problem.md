---
title: "XP =&gt; Ubuntu - problem"
date: 2008-02-27
forum: General Help
---

### Post by 5tv on 2008-02-27
Hello,

This is my first day I use Linux Ubuntu. Previous was Windows XP.
I must say it's very nice, but too difficult for me to understand...

Is it normal that I can't play any mp3's ?
I tried downloading aMsn & skype for linux, but neither of them seem to work.
In fact, eacht install gives me an error... When the download is an archive, and I read INSTALL - textfile, it's too difficult for me to understand these linux terms...

Could you guys give me a little help please ? :(

Greets,

5tv

---

### Post by chalewa on 2008-02-27
hi welcome to ubuntu

what are you using to play mp3? i personally use xmms (a lot like winamp)

you can get it by typing this in a terminal 

```
 sudo apt-get install xmms
```

as far as instant messaging goes, pidgin is probably your best bet. 

```
sudo apt-get install pidgin
```


and i am not too sure if skype is in the repositories or not, i think it probably is so try this for skype

```
sudo apt-get install skype
```




edit: or you can do all of this graphically using synaptic package manager, which is located in the system menu.

---

### Post by Arwen on 2008-02-27
Hello and Welcome!
You can also try emesene or Kopete for MSN chat client.
[Here's ]("http://www.skype.com/download/skype/linux/") the latest stable version of skype.

Don't worry,there are lots of things to learn but there are people willing to help you around here :-)

---

### Post by Crooksey on 2008-02-27
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by 5tv on 2008-02-27
Thanks for the quick reactions, but I don't where to enter those codes...

And the links to skype I found allready, but I get an ERROR while installing ...

Jesus, first time linux is difficult :(

---

### Post by Woe_is_me on 2008-02-27
You have to use the 'Terminal' 
Go to
 'Applications' (top of screen)
    'Accessories'
        'Terminal'

You type it in there

---

### Post by 5tv on 2008-02-27
"couldn't find packet"

When manually downloading, when opening, its says : 

"dependancy is not satisfiable"

:(

---

### Post by Creative2 on 2008-02-27
hello 
read my signature for codec and that stuff

---

### Post by 5tv on 2008-02-27
Ubuntu 7.10
Synaptic

    *

      Go to Applications &#8594; Add/Remove...
    *

      Set Show: to All available applications
    *

      Search for ubuntu-restricted-extras and install it.




Can't install... It does nothing...

---

### Post by chalewa on 2008-02-27
> **5tv said:**
> "couldn't find packet"

When manually downloading, when opening, its says : 

"dependancy is not satisfiable"

:(

can you post exactly what comes out of the terminal?


like your input, and then output

---

### Post by chalewa on 2008-02-27
and this may be a silly question, but you are in fact connected to the internet correct?

---

### Post by 5tv on 2008-02-27
steve@PC:~$ sudo apt-get install skype
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
Reading state information... Klaar
E: Kon pakket skype niet vinden

It's in Dutch, i'll translate :

Packetlist being read ... Ready
E: Could't find skype packet

I am connected to the internet ... otherwise , I wouldn't be able to post anything right ?

---

### Post by chalewa on 2008-02-27
> **5tv said:**
> steve@PC:~$ sudo apt-get install skype
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
Reading state information... Klaar
E: Kon pakket skype niet vinden

It's in Dutch, i'll translate :

Packetlist being read ... Ready
E: Could't find skype packet

I am connected to the internet ... otherwise , I wouldn't be able to post anything right ?

haha yea i literally laughed outloud after i came to that realization. 


and as far as the skype thing goes, that just means it is not in the repositories (the place where apt-get gets all its software from. )

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

type that into the terminal then type

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

then try to do 

```
sudo apt-get install skype
``` again. 



also, i assume that you are using gutsy.

---

### Post by 5tv on 2008-02-27
yes

---

### Post by .nedberg on 2008-02-27
I _think_ I know your problem!

Start Synaptic Package Manager (it will ask for your password), go to Settings -> Repositories.

On the tab "Ubuntu software" make sure everything is selected. On the updates tab "important" and "Recommended" should be selected.

Now press "Close" and the let it reload your sources.

Try to install Skype now, either from terminal or use Synaptic.

---

### Post by 5tv on 2008-02-27
OK .nedberg, this helped me a lot.
I can listen to music and talk on skype... :D

---

### Post by .nedberg on 2008-02-27
Glad I could help!

What happened was that your computer probably didn't have a Internet connection when you installed. For some reason the installer then disables all the repositories.

Easy fix though! And welcome to the land of Ubuntu Linux!

---

