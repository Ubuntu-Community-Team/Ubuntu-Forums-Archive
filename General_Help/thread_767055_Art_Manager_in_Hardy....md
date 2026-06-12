---
title: "Art Manager in Hardy..."
date: 2008-04-25
forum: General Help
---

### Post by Clayton South on 2008-04-25
I just did a fresh install of Hardy. When I load the Art Manager application and try to install new wallpapers, it crashes. I'm sure that I'm not the only one who noticed this. While it doesn't crash when I select the wallpaper and click "just download", it crashes when I click "install."

And this happens with or without graphics effects enabled (I tried both).

Anyone else have this problem?

-Clayton South

---

### Post by Clayton South on 2008-05-01
bump

---

### Post by Clayton South on 2008-05-06
I don't want to keep bumping up my question, but so far no one has given any feedback. Does anyone have any ideas here?

Thanks!

-Clayton South

---

### Post by NobleSavage on 2008-05-09
I'm having the same issue.

---

### Post by profediego on 2008-05-09
I try to run the art manager from command line and i get this, hope someone sees it and tell us how to fix it...

 $  gnome-art 
/usr/lib/ruby/1.8/open-uri.rb:277:in `open_http': 502 Bad Gateway (OpenURI::HTTPError)
	from /usr/lib/ruby/1.8/open-uri.rb:616:in `buffer_open'
	from /usr/lib/ruby/1.8/open-uri.rb:164:in `open_loop'
	from /usr/lib/ruby/1.8/open-uri.rb:162:in `catch'
	from /usr/lib/ruby/1.8/open-uri.rb:162:in `open_loop'
	from /usr/lib/ruby/1.8/open-uri.rb:132:in `open_uri'
	from /usr/lib/ruby/1.8/open-uri.rb:518:in `open'
	from /usr/lib/ruby/1.8/open-uri.rb:30:in `open'
	from /usr/lib/ruby/1.8/gnome-art/gnome_art.rb:156:in `isConnected'
	from /usr/lib/ruby/1.8/gnome-art/gnome_art.rb:132:in `main'
	from /usr/bin/gnome-art:25

---

### Post by mick316 on 2008-05-09
Same for me with Gutsy - Maybe the server is down or something ?

---

### Post by airxart on 2008-05-09
the splash screen program works by the same author.
This is all I get when I run it from terminal. No GUI shows

 gnome-art
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


The authors web site reports that it is not maintained anymore & suggests
another program.:confused:

---

### Post by airxart on 2008-05-10
I had it working in gutsy before I upgraded.
I had it working in hardy, but I was also trying to get my display driver, compiz &
terminal fixed. Which I did. As a result, now art manager doesn't work.
I guessing it conflicting with the display driver.
It shows it is connected in the terminal, but I see nothing. No GUI.
I see it try to display for a second the first time I run it.
 The splash screen program works. (same author)

---

### Post by Clayton South on 2008-05-12
Thanks for replying everyone...it seems that I'm not the only one with this problem or a similar one.

Can we submit this as a bug?

-Clayton South

---

### Post by airxart on 2008-05-18
Ideas, anyone?

Bump

---

### Post by HelloImHowie on 2008-05-18
[http://ubuntuforums.org/showthread.php?t=787488](http://ubuntuforums.org/showthread.php?t=787488)

---

