---
title: "Music Server, advice?"
date: 2007-01-28
forum: General Help
---

### Post by qalimas on 2007-01-28
I've switched bedrooms with my little brother, and now have a small room, meaning I no longer have my desktop, he does.  I still have my laptop however.  My situation is as follows... I have 7.1 speakers, that have three plugs to go to a computer, and in my Desktop, I had a 5.1 soundcard to hook them into.  They can not hook into my laptop.  I removed my sound card, and put it in an old 866 Celeron.  I plan to set this computer in a corner and use it just for my sound, and would like to be able to control it using my laptop.  I'd like to have an interface similar to Amarok that I can control what plays.

Is there a good music serving program I can use, or would it be best to put Amarok on it, and find the Amarok web interface to use?  (I'm a Kubuntu person.)

Thanks for any advice? =)

---

### Post by jimbren on 2007-01-29
It's not exactly what you're looking for, but you might want to consider using [gnump3d]("http://www.gnu.org/software/gnump3d/") as a streaming mp3 server.  

This will allow you to view your music via a web interface and stream it pretty seamlessly. I use Kubuntu as well, and I've found the Amorak doesn't always play well with m3u files from the server.  I am not really concerned enough to mess with it, so I use xmms to play from linux.  Windows Media Player or Winamp work well from windows machines.

You could also consider [Kplaylist]("http://www.kplaylist.net").  Kplaylist is a bit more complicated to initially set up, as it requires you to run Apache, Mysql and PHP, but installation of Kplaylist itself is a snap--just load the php file into your browser and point it to your collection.  

I can stream to Amorak with Kplaylist without any problems, for some reason. 

Either one should work okay with the system you've got--I am running Gnump3d on a P3 500 with only 128MB of RAM, and I can do a few streams at once on my local network without any hassles.


jimbo.

---

### Post by btdown on 2007-02-01
I'd use Slimserver...

More info in this thread:
[http://www.ubuntuforums.org/showthread.php?t=350782&highlight=mp3+server](http://www.ubuntuforums.org/showthread.php?t=350782&highlight=mp3+server)

---

### Post by Marsolin on 2007-02-02
If you are just looking for a media server you could try [Jinzora]("http://linuxappfinder.com/package/jinzora"), but from what you describe it doesn't sound like you need the computer to stream music, just play it.

If that is the case you could always load Amarok on that Celeron system and use Krdc to log into it from your laptop. It's the simple solution with software already install in Kubuntu and allows you to use Amarok for the playback and music management.

---

