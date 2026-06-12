---
title: "play Counter-Strike etc. In Direct9/10"
date: 2007-07-14
forum: General Help
---

### Post by Hottshot3312 on 2007-07-14
Hi,  I am thinking of Switching over to Ubuntu.  But I am a Heavy gamer,  I play HL2 CSS and many power hogging games.  I have a aweomse machine and I love to play my games at top notch settings,  Can crossover handle DX10/9  or Cedega?  And can cedega handle toontown, or crossover handle toontown?

---

### Post by Hottshot3312 on 2007-07-14
Bump

---

### Post by Hottshot3312 on 2007-07-14
hello?

---

### Post by Hippu on 2007-07-14
Wine (the program CrossOver is based on) works with Counter-Strike Source and Half-Life 2. 
CrossOver is commercial, but is probably easier to set up. But you might not be so lucky with toontown (See: [http://appdb.winehq.org/appview.php?iVersionId=5393](http://appdb.winehq.org/appview.php?iVersionId=5393)).

Cedega should too support CSS and HL2, but i don't know about toontown.

---

### Post by Hottshot3312 on 2007-07-14
> **Hippu said:**
> Wine (the program CrossOver is based on) works with Counter-Strike Source and Half-Life 2. 
CrossOver is commercial, but is probably easier to set up. But you might not be so lucky with toontown (See: [http://appdb.winehq.org/appview.php?iVersionId=5393](http://appdb.winehq.org/appview.php?iVersionId=5393)).

Cedega should too support CSS and HL2, but i don't know about toontown.

How good is D3D support, 9?  And do you have any suggestions about toontown?:confused:

---

### Post by Middle_Man on 2007-07-14
well, i personaly use windows to just play games on, i use ubuntu for everything else so ya... i would like to learn my self how to make these games compatible with ubuntu.

---

### Post by Hottshot3312 on 2007-07-14
> **Middle_Man said:**
> well, i personaly use windows to just play games on, i use ubuntu for everything else so ya... i would like to learn my self how to make these games compatible with ubuntu.

I was thinking about dual booting, as i have a 250 gig HD.



What about VMware, how laggy would that be with games, since it could run DX9 with everything else, toontown, etc.

---

### Post by Hottshot3312 on 2007-07-14
bump

---

### Post by Mongoose.wa on 2007-07-14
I don't have much firsthand experience with it yet, but from what I've read, games running through Wine run just as well as they would on Windows. I installed Steam on my Ubuntu computer last night without a hitch. I haven't played anything yet though, because there's some sort of bug with the font(s). I think I got a bad Tahoma.ttf or something.

Bottomline, most Windows games are perfectly playable in Linux through Wine, but they require work to run properly. People on these forums and others will surely be enough of a resource to get stuff working for you, but if you're not willing to put in effort tweaking stuff, etc, then I'd go with a dual-boot.

Another thing, I've heard [Wine-doors](http://www.wine-doors.org/wordpress/) is handy for installing/loading Windows apps.

---

### Post by Middle_Man on 2007-07-14
> **Mongoose.wa said:**
> I don't have much firsthand experience with it yet, but from what I've read, games running through Wine run just as well as they would on Windows. I installed Steam on my Ubuntu computer last night without a hitch. I haven't played anything yet though, because there's some sort of bug with the font(s). I think I got a bad Tahoma.ttf or something.

Bottomline, most Windows games are perfectly playable in Linux through Wine, but they require work to run properly. People on these forums and others will surely be enough of a resource to get stuff working for you, but if you're not willing to put in effort tweaking stuff, etc, then I'd go with a dual-boot.

Another thing, I've heard [Wine-doors](http://www.wine-doors.org/wordpress/) is handy for installing/loading Windows apps.

hay pall, i just got wine installed and i would like to know how to get steam up and running. can you show me how you got it run. i went to the steam website and downloaded the thing. i got a .msi file and i never had seen that one before... i just downloaded the latest ubuntu OS a few days ago and after 3-4 days i managed to do an overhaul getting it to play anything and everything. now i wanna try my hands at games. can ya hook me up? should i try out that wine door program?

thanks goes to anyone in advance who helps me out.

---

### Post by Hottshot3312 on 2007-07-14
does anyone know if IE7 can be run through wine?

---

### Post by Hottshot3312 on 2007-07-14
Wait,can wine do DX9?

---

### Post by Middle_Man on 2007-07-14
> **Hottshot3312 said:**
> Wait,can wine do DX9?

dude.... i just now heard about wine doors... i jumped in and tried it out for my self with no one helping and it worked 100% yes you can get dx9 to work, and steam as well. this is what you have to do though, follow me step by step and it should all work. i am assuming you are using A ubuntu distribution k. 

OPEN YOUR TERMINAL FIRST
we will install WINE on your PC ok.
Copy and Past this (COPY EVERYTHING in the quote box, not just the orange link and it should work, its common mistake that lots of new guys make)

> wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

now, depending on which vertion of ubuntu you are using, copy and past ONE of these

> For Ubuntu Feisty (7.04):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list

For Ubuntu Edgy (6.10): *64-bit packages not available*
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list](http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list) -O /etc/apt/sources.list.d/winehq.list

For Ubuntu Dapper (6.06): *64-bit packages not available*
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list](http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list) -O /etc/apt/sources.list.d/winehq.list

For Debian Etch (4.0): *64-bit packages not available*
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/etch.list](http://wine.budgetdedicated.com/apt/sources.list.d/etch.list) -O /etc/apt/sources.list.d/winehq.list


NOW copy and past this into your terminal

> sudo apt-get update

NOW copy and past this into your terminal once you did that last one
> 
sudo apt-get install wine

it should all work out just fine.

NOW WE WILL GET WINE DOORS INSTALLED IN ORDER TO GET ALL OF YOUR WINDOWS APPS INSTALLED WITH EASE :-D

go to this website
[http://www.wine-doors.org/wordpress/](http://www.wine-doors.org/wordpress/)

then click on the download section

there they will tell you there current release.

Current Release: Wine-Doors 0.1 (Vinegar Finger)
Tarball
Debian/Ubuntu

do not click the tarball link. instead click the Debian/Ubuntu link there. you should download the package just fine. once you got it, RIGHT click on it and select the 1st option that pops up. it should say something like Open With "Gdebi package installer" everything should take care of itself for a while. it may be a bit long. 

it will then ask you for your name and company (im assuming you are not using your computer for any company so just type N/A for the company section) procede and you should end up in something that looks simmiler to Synaptic package manager. 

THE FIRST THING YOU SHOULD DOWNLOAD!!!!!!!!

scroll down and you will find a few fonts ready for download. get ALL of them first. from that point on select what ever apps you want. it may take a while to get them installed but this should work.

---

### Post by Hottshot3312 on 2007-07-14
> **Middle_Man said:**
> dude.... i just now heard about wine doors... i jumped in and tried it out for my self with no one helping and it worked 100% yes you can get dx9 to work, and steam as well. this is what you have to do though, follow me step by step and it should all work. i am assuming you are using A ubuntu distribution k. 

OPEN YOUR TERMINAL FIRST
we will install WINE on your PC ok.
Copy and Past this (COPY EVERYTHING in the quote box, not just the orange link and it should work, its common mistake that lots of new guys make)



now, depending on which vertion of ubuntu you are using, copy and past ONE of these


NOW copy and past this into your terminal



NOW copy and past this into your terminal once you did that last one


it should all work out just fine.

NOW WE WILL GET WINE DOORS INSTALLED IN ORDER TO GET ALL OF YOUR WINDOWS APPS INSTALLED WITH EASE :-D

go to this website
[http://www.wine-doors.org/wordpress/](http://www.wine-doors.org/wordpress/)

then click on the download section

there they will tell you there current release.

Current Release: Wine-Doors 0.1 (Vinegar Finger)
Tarball
Debian/Ubuntu

do not click the tarball link. instead click the Debian/Ubuntu link there. you should download the package just fine. once you got it, RIGHT click on it and select the 1st option that pops up. it should say something like Open With "Gdebi package installer" everything should take care of itself for a while. it may be a bit long. 

it will then ask you for your name and company (im assuming you are not using your computer for any company so just type N/A for the company section) procede and you should end up in something that looks simmiler to Synaptic package manager. 

THE FIRST THING YOU SHOULD DOWNLOAD!!!!!!!!

scroll down and you will find a few fonts ready for download. get ALL of them first. from that point on select what ever apps you want. it may take a while to get them installed but this should work.
Oh my Gord,  THIS IS AWESOME, and one mistake you may want to fix, in the place where you pick packages for specific OS version fiesty etc, remove the ... from the link, got me.



and thank you. :)

---

### Post by Hottshot3312 on 2007-07-14
Hold on, do i have to install the Directx 9 runtime librarys?

---

### Post by BlahMan_of.Doom on 2007-07-18
Middle_Man you're so AWESOME :guitar:

I'll let you know how it goes.

It gives me this error everytime I try to start up Wine-doors:
```
$ sudo wine-doors 
Started logging session
Checking wine drive: /home/sixthelement/.wine/
Traceback (most recent call last):
  File "/usr/bin/wine-doors", line 99, in <module>
    ui.winedoors = ui.WineDoorsGUI()
  File "/usr/share/wine-doors/src/ui.py", line 920, in __init__
    self.tree = PackTree( self.window['tv_packlist'], self.window )
  File "/usr/share/wine-doors/src/ui.py", line 460, in __init__
    packlist.UpdateAll()
  File "/usr/share/wine-doors/src/packlist.py", line 284, in UpdateAll
    self.Update( ''.join( item[0:1] ) )
  File "/usr/share/wine-doors/src/packlist.py", line 266, in Update
    self.Parse( local_file )
  File "/usr/share/wine-doors/src/packlist.py", line 231, in Parse
    parser.parse( xmlfile )
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/expatreader.py", line 109, in parse
    xmlreader.IncrementalParser.parse(self, source)
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/xmlreader.py", line 123, in parse
    self.feed(buffer)
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/expatreader.py", line 216, in feed
    self._parser.Parse(data, isFinal)
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/expatreader.py", line 396, in external_entity_ref
    "")
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/saxutils.py", line 523, in prepare_input_source
    f = urllib2.urlopen(source.getSystemId())
  File "/usr/lib/python2.5/urllib2.py", line 121, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.5/urllib2.py", line 374, in open
    response = self._open(req, data)
  File "/usr/lib/python2.5/urllib2.py", line 392, in _open
    '_open', req)
  File "/usr/lib/python2.5/urllib2.py", line 353, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.5/urllib2.py", line 1100, in http_open
    return self.do_open(httplib.HTTPConnection, req)
  File "/usr/lib/python2.5/urllib2.py", line 1075, in do_open
    raise URLError(err)
urllib2.URLError: <urlopen error (111, 'Connection refused')>
```
I tried it with and without sudo.

---

