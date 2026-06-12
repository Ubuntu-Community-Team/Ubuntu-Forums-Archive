---
title: "gtk-apps.org Problem."
date: 2013-05-21
forum: General Help
---

### Post by stinkeye on 2013-05-21
I'm subscribed to gtk-apps.org rss feed for new content and receive feed news ok
but for the last couple of weeks the site won't load.
Is it just me?
[**_[COLOR="#B22222"]http://gtk-apps.org/ [/COLOR]_**]("http://gtk-apps.org/")

---

### Post by cipherboy_loc on 2013-05-21
I tried loading the page, but it didn't seem to load. In the bottom left corner of Firefox, it hung on "Connecting to static.gtk-apps.org", so I tried the following:

```

**cipherboy@ubuntu-basement:~$** ping gtk-apps.org
PING gtk-apps.org (188.138.118.86) 56(84) bytes of data.
64 bytes from gtk (188.138.118.86): icmp_req=1 ttl=53 time=142 ms
64 bytes from gtk (188.138.118.86): icmp_req=2 ttl=53 time=143 ms
64 bytes from gtk (188.138.118.86): icmp_req=3 ttl=53 time=143 ms
^C
--- gtk-apps.org ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 142.930/143.328/143.714/0.541 ms
**cipherboy@ubuntu-basement:~$** ping static.gtk-apps.org
PING static.gtk-apps.org (80.190.241.68) 56(84) bytes of data.
^C
--- static.gtk-apps.org ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 4999ms

**cipherboy@ubuntu-basement:~$** wget gtk-apps.org
--2013-05-21 17:06:37--  http://gtk-apps.org/
Resolving gtk-apps.org (gtk-apps.org)... 188.138.118.86
Connecting to gtk-apps.org (gtk-apps.org)|188.138.118.86|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: ‘index.html’

    [   <=>                                 ] 117,936      154KB/s   in 0.7s   

2013-05-21 17:06:38 (154 KB/s) - ‘index.html’ saved [117936]

**cipherboy@ubuntu-basement:~$** cat index.html 
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
**{snip}**
<script type='text/javascript' src='http://kona.kontera.com/javascript/lib/KonaLibInline.js'>
</script>
<!-- end Kontera(TM) --> 
</body></html>
**cipherboy@ubuntu-basement:~$**  wget static.gtk-apps.org
--2013-05-21 17:10:26--  http://static.gtk-apps.org/
Resolving static.gtk-apps.org (static.gtk-apps.org)... 80.190.241.68
Connecting to static.gtk-apps.org (static.gtk-apps.org)|80.190.241.68|:80... ^C
**cipherboy@ubuntu-basement:~$ **

```

In other words...the site proper is fine, but the content off of static.gtk-apps.org doesn't seem to work, at least for me. 


Thanks,
Cipherboy LOC

---

### Post by stinkeye on 2013-05-22
> **cipherboy_loc said:**
> I tried loading the page, but it didn't seem to load. In the bottom left corner of Firefox, it hung on "Connecting to static.gtk-apps.org", so I tried the following:

```

**cipherboy@ubuntu-basement:~$** ping gtk-apps.org
PING gtk-apps.org (188.138.118.86) 56(84) bytes of data.
64 bytes from gtk (188.138.118.86): icmp_req=1 ttl=53 time=142 ms
64 bytes from gtk (188.138.118.86): icmp_req=2 ttl=53 time=143 ms
64 bytes from gtk (188.138.118.86): icmp_req=3 ttl=53 time=143 ms
^C
--- gtk-apps.org ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 142.930/143.328/143.714/0.541 ms
**cipherboy@ubuntu-basement:~$** ping static.gtk-apps.org
PING static.gtk-apps.org (80.190.241.68) 56(84) bytes of data.
^C
--- static.gtk-apps.org ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 4999ms

**cipherboy@ubuntu-basement:~$** wget gtk-apps.org
--2013-05-21 17:06:37--  http://gtk-apps.org/
Resolving gtk-apps.org (gtk-apps.org)... 188.138.118.86
Connecting to gtk-apps.org (gtk-apps.org)|188.138.118.86|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: &#8216;index.html&#8217;

    [   <=>                                 ] 117,936      154KB/s   in 0.7s   

2013-05-21 17:06:38 (154 KB/s) - &#8216;index.html&#8217; saved [117936]

**cipherboy@ubuntu-basement:~$** cat index.html 
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
**{snip}**
<script type='text/javascript' src='http://kona.kontera.com/javascript/lib/KonaLibInline.js'>
</script>
<!-- end Kontera(TM) --> 
</body></html>
**cipherboy@ubuntu-basement:~$**  wget static.gtk-apps.org
--2013-05-21 17:10:26--  http://static.gtk-apps.org/
Resolving static.gtk-apps.org (static.gtk-apps.org)... 80.190.241.68
Connecting to static.gtk-apps.org (static.gtk-apps.org)|80.190.241.68|:80... ^C
**cipherboy@ubuntu-basement:~$ **

```

In other words...the site proper is fine, but the content off of static.gtk-apps.org doesn't seem to work, at least for me. 


Thanks,
Cipherboy LOC

Yep, that's what I'm seeing.
My browser stalls at **Connecting to remote host static.gtk-apps.org**
and has been like that for a couple of weeks.
The kde-apps.org site loads fine.
Sent an email to opendesktop.org

---

### Post by vasa1 on 2013-05-22
@stinkeye, I edited my /etc/hosts file to include
127.0.0.1  [http://static.gtk-apps.org](http://static.gtk-apps.org)

I did this because while the link you provided doesn't load (as we've seen), I could use Ctr+U to view the source of the page. That had this:
h t t p : / / static.gtk-apps.org/styles/global-style.css and some other stuff that may not be crucial to the content. 

So when I tried to load your link again with the modified hosts file, it loaded without styles and presumably some fancy javascript stuff.

---

### Post by stinkeye on 2013-05-22
> **vasa1 said:**
> @stinkeye, I edited my /etc/hosts file to include
127.0.0.1  [http://static.gtk-apps.org](http://static.gtk-apps.org)

I did this because while the link you provided doesn't load (as we've seen), I could use Ctr+U to view the source of the page. That had this:
h t t p : / / static.gtk-apps.org/styles/global-style.css and some other stuff that may not be crucial to the content. 

So when I tried to load your link again with the modified hosts file, it loaded without styles and presumably some fancy javascript stuff.
Hi, **vasa1**...
Yeah that seems to work. Bit messy but readable and dowload links still work.
At least the page loads when I click on a link in the RSS feed.
Thanks.

Edit: Thanks also to **cipherboy_loc** for your input.

---

### Post by vasa1 on 2013-05-22
> **stinkeye said:**
> Hi, vasa1...
Yeah that seems to work. Bit messy but readable and dowload links still work.
At least the page loads when I click on a link in the RSS feed.
Thanks.
Glad I could help. Someone needs to fix that site. It's quite informative!

I visited it with Google Chrome 27 thinking I might be luckier. But that browser just had "sending request" in its status bar. Firefox showed the link which was the "blocker" in its status bar so I knew what to look for in the source.

Edit:
I don't use /etc/hosts normally and I think
127.0.0.1 static.gtk-apps.org
would be the appropriate thing.

---

### Post by stinkeye on 2013-05-22
> **vasa1 said:**
> Glad I could help. Someone needs to fix that site. It's quite informative!

I visited it with Google Chrome 27 thinking I might be luckier. But that browser just had "sending request" in its status bar. Firefox showed the link which was the "blocker" in its status bar so I knew what to look for in the source.

Edit:
I don't use /etc/hosts normally and I think
127.0.0.1 static.gtk-apps.org
would be the appropriate thing.
Yep I use the same thing to block **vindsl.com** so I don't have to load his 1Mb conky screenshots everytime
he changes his wallpaper.
That's just between you and me, though. 
:-$ 8-[

---

