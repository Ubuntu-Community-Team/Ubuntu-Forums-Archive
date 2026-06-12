---
title: "dpkg not work"
date: 2005-10-21
forum: General Help
---

### Post by minh on 2005-10-21
hi, 
i'm having a problem while installing programme
once i've installed mplayer with apt-get
then it can't find one package, and since then everytime i go with apt-get it runs 

Setting up w32codecs (20050412+breezy0.0.1) ...
--20:03:41--  [http://www1.mplayerhq.hu/MPlayer/releases/codecs/windows-all-20050412.zip](http://www1.mplayerhq.hu/MPlayer/releases/codecs/windows-all-20050412.zip)
           => `windows-all-20050412.zip'
Connecting to 195.83.11.66:3128... connected.

and it stops.:mad: 
can you tell me what to do 
(sudo dpkg -f install have same pb)

---

### Post by Kyral on 2005-10-21
try

```
sudo apt-get -f install
```

---

### Post by minh on 2005-10-21
hi,

sudo apt-get -f install

have same pb :(

---

### Post by Kyral on 2005-10-21
Okay.

Try installing w32codecs with this method

[https://wiki.ubuntu.com/RestrictedFormats#head-ae79fed9d60ccdf06f400ae76ad53867d94bb2b8](https://wiki.ubuntu.com/RestrictedFormats#head-ae79fed9d60ccdf06f400ae76ad53867d94bb2b8)

---

### Post by minh on 2005-10-21
thanks,
but i don't have ftp working here
anyway i got w32codecs run now
but the message still exist

---

### Post by Kyral on 2005-10-21
"ftp not working"?

Unless its blocked off by a firewall (COMPLETELY) you should be able to download off FTP.

Anyway. Try reinstalling MPlayer.It might work. I don't know I don't use MPlayer

---

### Post by minh on 2005-10-21
> 
"ftp not working"?

Unless its blocked off by a firewall (COMPLETELY) you should be able to download off FTP.

Anyway. Try reinstalling MPlayer.It might work. I don't know I don't use MPlayer


the things that i want to ask that why apt-get install * doesn't work
how do I get it work again:neutral:

---

### Post by Kyral on 2005-10-21
*Mentally backs up and tried to reestablish whats going on, because he got himself confused*

Lemme list out the facts so I know whats going on now.

1) You tried to install MPlayer and it did this

 Setting up w32codecs (20050412+breezy0.0.1) ...
 --20:03:41--  [http://www1.mplayerhq.hu/MPlayer/rel...l-20050412.zip]("http://www1.mplayerhq.hu/MPlayer/releases/codecs/windows-all-20050412.zip")
            => `windows-all-20050412.zip'
 Connecting to 195.83.11.66:3128... connected.

2) You installed w32codecs and sudo apt-get -f install still gives you this

 Setting up w32codecs (20050412+breezy0.0.1) ...
 --20:03:41--  [http://www1.mplayerhq.hu/MPlayer/rel...l-20050412.zip]("http://www1.mplayerhq.hu/MPlayer/releases/codecs/windows-all-20050412.zip")
            => `windows-all-20050412.zip'
 Connecting to 195.83.11.66:3128... connected.

3) Apt-Get nor Synaptic work anymore. And you ARE connected to the internet

---

### Post by minh on 2005-10-21
> 
1) You tried to install MPlayer and it did this

Setting up w32codecs (20050412+breezy0.0.1) ...
--20:03:41-- [http://www1.mplayerhq.hu/MPlayer/rel...l-20050412.zip](http://www1.mplayerhq.hu/MPlayer/rel...l-20050412.zip)
=> `windows-all-20050412.zip'
Connecting to 195.83.11.66:3128... connected.

2) You installed w32codecs and sudo apt-get -f install still gives you this

Setting up w32codecs (20050412+breezy0.0.1) ...
--20:03:41-- [http://www1.mplayerhq.hu/MPlayer/rel...l-20050412.zip](http://www1.mplayerhq.hu/MPlayer/rel...l-20050412.zip)
=> `windows-all-20050412.zip'
Connecting to 195.83.11.66:3128... connected.

3) Apt-Get nor Synaptic work anymore. And you ARE connected to the internet


i'm sorry if i am not clear

---

### Post by Kyral on 2005-10-21
Nah, I've just been bouncing artound the Forums and helping a lot and I had to step back and make sure I was thinking of the right thing. Can't help you if I think you are someone else :D

---

### Post by minh on 2005-10-21
i don't have that stupid idea that you are thinking,
i just want to say you're right when listing all the enorme pbs that I have
I am a little unpatient, that's my faute 
i am a new bie, so I think you guys have many experiences could have this pb before and can help me,
maybe i have to reinstall ubuntu will work but it seems stupid:confused:

---

### Post by Ampersand on 2005-10-21
Hi
You might have more success installing them manually. 
Firstly, make a directory by opening a terminal and typing:
```
sudo mkdir /usr/lib/win32
```
Download [http://www1.mplayerhq.hu/MPlayer/releases/codecs/windows-all-20050412.zip](http://www1.mplayerhq.hu/MPlayer/releases/codecs/windows-all-20050412.zip), then extract them to your home directory.
Go back to the terminal, and copy them to the directory you created earlier using:
```
sudo cp ~/windows-all-20050412/* /usr/lib/win32/
```
using whatever directory you extracted the zip file to, it might be ~/Desktop/windows... (~ means your home directory).
It should then work, hopefully.

---

### Post by minh on 2005-10-22
> 
Firstly, make a directory by opening a terminal and typing:
Code:

sudo mkdir /usr/lib/win32

Download [http://www1.mplayerhq.hu/MPlayer/rel...l-20050412.zip](http://www1.mplayerhq.hu/MPlayer/rel...l-20050412.zip), then extract them to your home directory.
Go back to the terminal, and copy them to the directory you created earlier using:
Code:

sudo cp ~/windows-all-20050412/* /usr/lib/win32/



mplayer works always 
however I don't understand they still have to download this file each time I run apt-get install blabla
it can't download this file, so it blocks
but it can download from www2.mplayerhq..... insteand of www1.mplayerhq...

---

### Post by minh on 2005-10-22
thanks guys, it fixed now
quote:
sudo dpkg -r w32codecs

---

