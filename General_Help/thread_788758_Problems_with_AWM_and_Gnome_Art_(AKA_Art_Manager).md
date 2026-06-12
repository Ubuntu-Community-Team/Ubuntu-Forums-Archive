---
title: "Problems with AWM and Gnome Art (AKA Art Manager)"
date: 2008-05-10
forum: General Help
---

### Post by Carlo1973 on 2008-05-10
I have been having problems getting Gnome Art (IE: Art Manager) and AWM to work. AWM doesn't even launch for me at all when I choose it from the menu - not sure why. I've tried reinstalling it with no difference.

Art Manager "was" working - but only to the point where it was launching, and alowing me to select different available desktops, etc. However if I tried to install anything, it would close without performing any actions.


I have tried to download Gnome Art Manager Next Gen and installing it. I've tried the .deb package, and the source tar balls. If I try to launch GnomeArtNG, I get the following output in console:


dtUbuntu

(GnomeArtNg:8771): Gtk-CRITICAL **: gtk_window_resize: assertion `width > 0' fai
led

Unhandled Exception: System.IO.FileNotFoundException: Could not find file "/home
/carlo/.gnome2/gnome-art-ng/gnomeArt10.xml".
File name: '/home/carlo/.gnome2/gnome-art-ng/gnomeArt10.xml'
  at System.IO.FileStream..ctor (System.String path, FileMode mode, FileAccess a                                                                                                                                                            ccess, FileShare share, Int32 bufferSize, Boolean anonymous, FileOptions options                                                                                                                                                            ) [0x00000]
  at System.IO.FileStream..ctor (System.String path, FileMode mode, FileAccess a                                                                                                                                                            ccess, FileShare share) [0x00000]
  at (wrapper remoting-invoke-with-check) System.IO.FileStream:.ctor (string,Sys                                                                                                                                                            tem.IO.FileMode,System.IO.FileAccess,System.IO.FileShare)
  at System.Xml.XmlUrlResolver.GetEntity (System.Uri absoluteUri, System.String                                                                                                                                                             role, System.Type ofObjectToReturn) [0x00000]
  at Mono.Xml2.XmlTextReader.GetStreamFromUrl (System.String url, System.String&                                                                                                                                                             absoluteUriString) [0x00000]
  at Mono.Xml2.XmlTextReader..ctor (System.String url, System.Xml.XmlNameTable n                                                                                                                                                            t) [0x00000]
  at System.Xml.XmlTextReader..ctor (System.String url, System.Xml.XmlNameTable                                                                                                                                                             nt) [0x00000]
  at System.Xml.XmlDocument.Load (System.String filename) [0x00000]
  at GnomeArtNG.CArtManager.parseXMLFile () [0x00000]
  at GnomeArtNG.CArtManager.getParseAndCreate (Boolean ForceReload) [0x00000]
  at GnomeArtNG.CArtManager.set_ArtType (ArtType value) [0x00000]
  at GnomeArtNgApp.OnSwitchPage (System.Object sender, Gtk.SwitchPageArgs s) [0x                                                                                                                                                            00000]
  at GnomeArtNgApp..ctor (System.String[] args) [0x00000]
  at GnomeArtNgApp.Main (System.String[] args) [0x00000]



If anyone can help me get these running it would be awesome :)

thanks a bunch in advance :D

Carlo

---

### Post by FuturePilot on 2008-05-10
I'm not sure what's going on with Gnome Art Manager. But as for AWN, are you using Compiz? You need a composite manager running for AWN to work.

---

### Post by 1981Neo on 2008-05-10
Hi!

I am the author of Gnome-Art Next Gen. So I can confirm that this is happening...but unfortunately on every machine the program is installed. That's because the server art.gnome.org is sending wrong data (it closes the connection right after a "get" command (to be exact) ).

There already is a bug report on this on gnomeartng.berlios.de ... and the people at art.gnome.org are informed too! They are working on a solution on this!

So all you (and me) could do is sit and wait for a server-side solution :(

I'm just going to walk on the jacobs way... so I'll be away for the next 2 weeks from now on. Hope that this is fixed soon!

CU, greetings Tom

---

### Post by airxart on 2008-05-10
Thanks for the info.
I thought it was my machine.

---

### Post by jay_d1 on 2008-05-10
I really do hope this is resolved soon. I was just jumping up and down because i found this solution to the original gnome-art and now it doesn't work :-( Oh well, guess i'll have to wait.

---

### Post by Carlo1973 on 2008-05-11
> **FuturePilot said:**
> I'm not sure what's going on with Gnome Art Manager. But as for AWN, are you using Compiz? You need a composite manager running for AWN to work.
Regarding AWM - I am using Compiz. At least - I think I am :p I have it installed and I have the newest drivers installed for my SLI Nvidia card. I had chosen options for Compiz. So I think its running. 


Glad to know that I'm not the only one having problems with the Gnome Art Manager :) I thought I was going insane!!Have a good 2 weeks off 1981Neo!

---

### Post by guildofghostwriters on 2008-05-11
Would it be possible to either announce here when it's resolved or point us to a place where it will be announced?

Also, what's the jacobs way? Have a good time walking it!

---

### Post by MagicMoonLight on 2008-05-11
:(OMG Bad Luck.

I;m going to lose out on some potential customers who are instersted in using Ubuntu for OS with a new POS sytem for there business, I been trying to spread more linux and less windows and the business world because the systems are just better and have far less down time.

I trying to build my demonstration machine to show some clients tomorrow and now Im stuck with the very ugly Ubuntu default scheme is not going to impress anyone or im going to now have to force a manually installed theme into the system if find it on the web site.

People get it together don't let linux lose out over stupid stuff we all need to have are stuff up and going so linux can grow. Keep backup images of your server data in case something like this happens is important for system related updaters to always be available.

Also what is with weather.com widgets being off line for a week now this is annoying it make most normal people switch back to windows.

:confused::confused::confused::confused:

I hope someone reads this before we lose out worse on the system crash.

---

### Post by mangan on 2008-05-11
> **MagicMoonLight said:**
> :(OMG Bad Luck.

I;m going to lose out on some potential customers who are instersted in using Ubuntu for OS with a new POS sytem for there business, I been trying to spread more linux and less windows and the business world because the systems are just better and have far less down time.

I trying to build my demonstration machine to show some clients tomorrow and now Im stuck with the very ugly Ubuntu default scheme is not going to impress anyone or im going to now have to force a manually installed theme into the system if find it on the web site.

People get it together don't let linux lose out over stupid stuff we all need to have are stuff up and going so linux can grow. Keep backup images of your server data in case something like this happens is important for system related updaters to always be available.

Also what is with weather.com widgets being off line for a week now this is annoying it make most normal people switch back to windows.

:confused::confused::confused::confused:

I hope someone reads this before we lose out worse on the system crash.
If you're generally interested in getting info regarding the weather.com widgets, you're best off starting a new thread with your question.

As far as the rest goes, Compiz is currently working great. If you're worried about "the default ugly theme," Emerald theme manager works wonders. You can get new themes from [www.gnome-look.org](www.gnome-look.org) and rock out :)

I've never used gnome art manager, and I am FAR from the default orange/brown theme :).

---

### Post by mano cazalet on 2008-05-11
i believe weather.com widgets are working
saw a couple of threads on this issue

:evil:
and maybe it is not a good idea to leave this kind of customization for last day :evil:

evil off/

sorry had to say that, heard it so many times from my mum and never had the chance to say it to someone else

Hope that you manage to create a nice theme using [www.gnome-look.org](www.gnome-look.org) emerald and compiz

ps::)

---

### Post by MagicMoonLight on 2008-05-12
I'm sorry jabout my earlier post ust mad at the server being down but crap happens thats the way computers are sometime.

I used the gnome.org to get a better them but I thought it was a lot slower and harder than using gnome-art so I went and copied the files manually from my other linux machine and installed them and everything is OK. I just hope that this gets fixed soon it really was a pain in the butt what happened and what I did to make it work on the demo machine.

I want thank the community for the hard work in making this a good system that inspires people to turn from the corporate Microsoft to a more stable system. Anyways it not how it looks but how works that counts that what kept Linux kernel all these since the old days of computers.

thanks for the help people. :popcorn:

---

### Post by HDave on 2008-05-16
Wish I would have found this thread before spending two hours trying to reinstall and fix gnome-art myself.   I finally got the idea of launching it from within a terminal instead of the menu so I could see the error message, which for me is:

```

/usr/lib/ruby/1.8/net/protocol.rb:133:in `sysread': Connection reset by peer (Errno::ECONNRESET)
	from /usr/lib/ruby/1.8/net/protocol.rb:133:in `rbuf_fill'
	from /usr/lib/ruby/1.8/timeout.rb:56:in `timeout'
	from /usr/lib/ruby/1.8/timeout.rb:76:in `timeout'
	from /usr/lib/ruby/1.8/net/protocol.rb:132:in `rbuf_fill'
	from /usr/lib/ruby/1.8/net/protocol.rb:116:in `readuntil'
	from /usr/lib/ruby/1.8/net/protocol.rb:126:in `readline'
	from /usr/lib/ruby/1.8/net/http.rb:2020:in `read_status_line'
	from /usr/lib/ruby/1.8/net/http.rb:2009:in `read_new'
	 ... 10 levels...
	from /usr/lib/ruby/1.8/open-uri.rb:30:in `open'
	from /usr/lib/ruby/1.8/gnome-art/gnome_art.rb:156:in `isConnected'
	from /usr/lib/ruby/1.8/gnome-art/gnome_art.rb:132:in `main'
	from /usr/bin/gnome-art:25

```
You would think that gnome-art would be smart enough to tell you if it can't reach the server! :mad:

---

### Post by Carlo1973 on 2008-05-17
I think that was an oversight. It may be something that they will add in the next instance or patch. Let them get the thing working properly before they start adding additional functions. I have faith that they will eventually put in a redundency to prevent it from crashing if it can't connect to the network, maybe even with a popup error log to help determine why it cant connect.

---

### Post by 1981Neo on 2008-05-24
Hi @all,

:KS just wanted to point out that I recently fixed Gnome-Art Next Gen. 
@HDave: This is not a problem on the application site. Both applications do connect to the server. The problem is that art.gnome.org is closing the connection before sending data...it's a server error and not a normal behavior...Anyway I fixed it.

@airxart: I would not recommend using the old gnomeart...instead use the new gnomeartng...

Get the new version from gnomeartng.berlios.de ! All downloads are located at the project site -> files !

Information about the way I was walking is found [here]("http://whc.unesco.org/en/list/669"), our blog (in german) is located [here]("http://unserkleinespilgerblog.blogspot.com").

Have fun, donate if you wish and don't worry, be happy :)

Greetings, Tom

---

