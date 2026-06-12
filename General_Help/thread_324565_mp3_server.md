---
title: "mp3 server?"
date: 2006-12-23
forum: General Help
---

### Post by Roasted on 2006-12-23
How would I set one up? My buddy showed me his one time, and it had a good 2,000 songs or so up on this, well, this web site. You type in the IP, log in, and bam, I could listen to Motley Crue and ACDC all night.

Well, question. How do I do that? And is there a limit to how much music you can have on this server? I have considerably more than my buddy did, so I'm wondering if it's possible.

And how exactly does it work? I assume it's just remote access to my music folder? (meaning my pc has to be on all the time)??

---

### Post by iamhugeinjapan on 2006-12-23
You can use Rhythmbox to share your media library, as far as I know there is no limit. Does take a bit of config file editing unfortunately but it's nothing strenuous.

---

### Post by iamhugeinjapan on 2006-12-23
See this thread for tips
[http://www.ubuntuforums.org/showthread.php?t=252925&highlight=rhythmbox+daap](http://www.ubuntuforums.org/showthread.php?t=252925&highlight=rhythmbox+daap)

---

### Post by rbalfour on 2006-12-24
Are you talking about GNUMP3d ?

This is the streaming server I use for my music. Works in Windows/linux/mac.
LAN/WAN is fine too.

---

### Post by Roasted on 2006-12-24
Evidently gnump3d was already installed. But it won't launch. There's no icon for it, and synaptic says it's in with the latest version. If I Alt F2 and hit gnump3d and it still won't launch.

Then I did a terminal launch:


jason@jason:~$ sudo gnump3d
  Couldn't create the listening socket for receiving incoming
 requests upon

  Perhaps the port 8888 is already in use?

  This is the error message the system returned:

     Address already in use

jason@jason:~$



What in the world would be using port 8888?

---

### Post by FastZ on 2006-12-26
Gnump3d is web based.  Requires Apache Server to be installed on the maching to run.  If you have Apache installed on the server, then you can open a browser window on the computer your music is on and go to the URL [http://localhost:8888](http://localhost:8888) and it should bring up the gnump3d streaming media server page.  If not, then I would uninstall it from your system and apt-get install it again, then go into the gnump3d.conf file and make sure everything is working.  You can change what port it is being accessed by in the .conf file as well if you still cant get it to work on port 8888.

Oh and btw, Gnump3d isnt really a "program", more like a script of sorts, or maybe a webpage...but not a program so therefore you cant sudo gnump3d or run it from the alt+F2.;)

---

### Post by Roasted on 2006-12-26
I see. Am I supposed to use 8888? Or should I change the url to something else so that it's more secure? (I have no idea if I can even change it, I'm just assuming I can/should).

And also... how do I... well, upload the music to gnump3d?

As well as finding the config file...?

---

### Post by zanglang on 2006-12-26
You might want to check out their documentation page. ;)
[http://www.gnu.org/software/gnump3d/documents.html](http://www.gnu.org/software/gnump3d/documents.html)

---

### Post by Roasted on 2006-12-26
I must be in over my head, or just not looking in the right place. I read that link, and clicked around, yet... what I read told me nothing about how to get the music generated for the server. Am I looking in the wrong spot?

---

### Post by rbalfour on 2006-12-28
If the music server is on the same PC. Open a broswer to 

[http://localhost:8888](http://localhost:8888)

if on another box


http://<ip address>:8888

You still need to setup the config file for gnump, so it knows where you music is at.

This just out! [http://ubuntu-tutorials.com/2006/12/28/how-to-setup-gnump3d-for-a-streaming-media-server-ubuntu-510-6061-610/](http://ubuntu-tutorials.com/2006/12/28/how-to-setup-gnump3d-for-a-streaming-media-server-ubuntu-510-6061-610/)

Good How-to. gl

---

### Post by Roasted on 2006-12-29
Okay. I got to the config file and set up what I wanted to. First, I changed the port. Then I went to the browser and typed in [http://localhost:7896](http://localhost:7896)

I got page cannot be displayed.

I changed it back to 8888. Now I get the home screen of gnump3d. Weird? It even said, I can change my port if I choose. I did. And this?

Anyway, problem 2:

At one point, the how-to says this. "Find the line that says:

root = /var/music

and update it to the location of your media. (ie; in my situation I store the music in /media/music)"

My music is stored in my music folder, which is located right in my home folder. I changed the path to /home/music. Nothing changed. /home/jason/music, nothing. /jason/music, nothing either. What am I doing wrong?

---

### Post by mscman on 2006-12-31
Did you relaunch the gnump3d daemon? Run:
```
sudo /etc/init.d/gnump3d restart
``` after you make changes to the configuration file.

---

### Post by Roasted on 2006-12-31
Oh cool, thanks bud. It works now!

Now if I go to school and want to log in to my music, do I just put my computers IP address in instead of the default 8888?

---

### Post by electricshoes on 2006-12-31
You should check out Ampache ([http://ampache.org](http://ampache.org))

I use it on a Ubuntu LAMP server, its super slick. Even has a flash player.

> Ampache is a PHP-based tool for managing, updating and playing your MP3/OGG/RM/FLAC/WMA/M4A files via a web interface. It allows you to save playlists, create user accounts, and share your music catalogs with other Ampache servers

---

### Post by Roasted on 2006-12-31
What do I use to connect to gnump3d from elsewhere? I use my IP address right? Trying that but it aint working, however I'm sure I'm doing something wrong. ](*,)

---

### Post by mscman on 2007-01-01
> **Roasted said:**
> What do I use to connect to gnump3d from elsewhere? I use my IP address right? Trying that but it aint working, however I'm sure I'm doing something wrong. ](*,)

It sounds like I'm in a similar situation to yourself. I haven't been able to test the streaming locally, since the box is at a friend's house (I'm trying to set up the streaming server for him.) The interface shows all of the audio files and all is well, but when I try to play the music, it doesn't play... It opens iTunes and just quits.

I'll keep you posted if I make any progress. I will also probably try [A]mpache as suggested in the post preceding yours to see which I like better.

---

### Post by Roasted on 2007-01-01
Mine works locally. I just don't know what to do if I go to school. Like, what I would put in the address bar in order to GET to my "account" to listen to the music.

---

### Post by Roasted on 2007-01-02
Okay. So I understand I have to forward the port in my router to my local machine, then use my actual IP address:Port in order to connect to the mp3 stream.

I forwarded my port, or so I think. Does it look okay?


The reason I ask if it looks okay is because... well... IT DOESN'T WORK! ](*,) 


[IMG]http://i2.photobucket.com/albums/y36/Roasted/gnump3dscreenie.jpg[/IMG]

---

### Post by electricshoes on 2007-04-12
I don't see why that wouldn't work if you were forwarding the port properly. You could also setup a VPN and use something like [Hamachi]("http://ubuntuforums.org/showthread.php?t=135036&highlight=hamachi") so that you wont have to forward any ports.

---

### Post by Roasted on 2007-04-13
This thread is kind of old. I forgot about it. I realized that my router was bugged and got rid of it and picked up a Linksys router. Now everything runs smoothly, however I haven't gotten Gnump3d to work yet.

Again I forgot this thread was even out here, so I had posted a new one. But check out this thread and tell me what you think. Still waiting on responses. :( 

[http://ubuntuforums.org/showthread.php?t=404502](http://ubuntuforums.org/showthread.php?t=404502)

---

