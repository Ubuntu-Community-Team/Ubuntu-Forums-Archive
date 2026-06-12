---
title: "shell script question"
date: 2013-08-17
forum: General Help
---

### Post by macey on 2013-08-17
Hello, I am no shell script expert but have been dabbling for some time.
I have a routine that I user for killing selected tasks:-
```

for i in `ps aux|grep  "vlc" |grep -v grep | awk '{print $1}' ` ; do
          kill -9 $i
          done

```
On my arm linux machine (Nokia N900)

```
ps aux|grep  "vlc" |grep -v grep
```

would typically return:-
```

19716 user     81648 S    /opt/VideoLAN/bin/vlc -I dummy --volume 120 http://name:password@localhost:9981/stream/channelid/60

```

Executing the kill code would kill task 19716 successfuly.

If I modify the code in any way to be more selective in killing my vlc task, sometihing like:-
```

for i in `ps aux|grep  "vlc -I dummy --volume 120 http://name:password@localhost:9981/stream/channelid" |grep -v grep | awk '{print $1}' ` ; do
          kill -9 $i
          done
```

```
ps aux|grep  "vlc -I dummy --volume 120 http://name:password@localhost:9981/stream/channelid" |grep -v grep
```
returns:-

```
19716 user     81648 S    /opt/VideoLAN/bin/vlc -I dummy --volume 120 http://name:password@localhost:9981/stream/channelid/60
```

But executing the modified "kill loop" code does not kill task 19716.

Anyone here able to tell me why?
I have changed the code in any number of ways to select just this type  of vlc task, using grep "9981*, grep "stream"..... Only grep "vlc" seems to work.
I thought I knew how this code worked, very myserious!:confused::confused:

---

### Post by Lars Noodén on 2013-08-17
There's a utility called [pgrep](http://manpages.ubuntu.com/manpages/raring/en/man1/pgrep.1.html).  Does that do what you want?  Note that there is also an option (-x) for exact matches not just patterns.

Or are you writing a whole script on principle?

---

### Post by evilsoup on 2013-08-17
I had a very similar function in my .bashrc, until I discovered that I could just use the commands 'killall' or 'pgrep'/'pkill'.

```
pkill -f 'vlc -I dummy --volume 120 http://name:password@localhost:9981/stream/channelid'
```

I'm not sure why you command actually breaks, though.

---

### Post by macey on 2013-08-17
> **evilsoup said:**
> I had a very similar function in my .bashrc, until I discovered that I could just use the commands 'killall' or 'pgrep'/'pkill'.

```
pkill -f 'vlc -I dummy --volume 120 http://name:password@localhost:9981/stream/channelid'
```

I'm not sure why you command actually breaks, though.

That does it , thanks.

---

