---
title: "gnome-art manager fails to start in hardy"
date: 2008-05-11
forum: General Help
---

### Post by robert shearer on 2008-05-11
system=>preferences=>art manager causes a window to open on the desktop for about a nano-second and  then it closes and nothing happens.

Running gksudo gnome-art in a terminal gives the following;

Create Backgrounds-File
Create program-folder
Create thumbnail-folder
Create temp-folder
Create download-folder
Create backgrounds-folder
Create splashscreens-folder
Create themes-folder

then returns to a prompt and again nothing happens.

Used to work fine in Gutsy.

This is a fresh install of Hardy with all updates.

Can any-one help please ?

---

### Post by micdhack on 2008-05-11
same problem here...although error is different
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

---

### Post by guildofghostwriters on 2008-05-11
The problem is explained here - [http://ubuntuforums.org/showthread.php?t=788758](http://ubuntuforums.org/showthread.php?t=788758) - apparently it's something on the server side.

---

### Post by robert shearer on 2008-05-11
Wow, thanks so much for the speedy reply!.

 I see that the problem will be addressed and time and patience is my best action.

I am really enjoying Hardy. It seems to be smoother and better integrated than Gutsy and any concerns so far have been minor or, as with this, already been addressed.

Thanks again.

---

### Post by guildofghostwriters on 2008-05-11
You're welcome - but I just happened to see this thread after reading the other one. I'm new to Ubuntu and can only compare with Windows. I've had a few problems and it's occasionally been a challenge and a steep learning curve but I'm glad I swapped and can't see myself going back.

---

