---
title: "command-line bittorrent"
date: 2006-11-02
forum: General Help
---

### Post by Bachstelze on 2006-11-02
So basically, what I want to do is launch a BItTorrent download on a remote machine via SSH and then leave it alone. I've installed bittornado, use the btdownloadheadless command and if works fine, except that it stops when I log out of the system, so it's pretty much useless. Could anyone help me to get this working, i.e. continue to download when I log out ?

P.S. ; i've tried to add a & at the end of the command but ten the download doesn't even start :/

---

### Post by po0f on 2006-11-02
HymnToLife,

Your best bet would be to look into [screen](http://packages.ubuntu.com/edgy/misc/screen).

---

### Post by Bachstelze on 2006-11-02
Brilliant ! Exactly what I was looking for, thanks !

---

### Post by theonlyalterego on 2007-06-28
My question: how do i check the status of a backgrounded btdownloadheadless.bittornado process?

The "Fully Story":
So I poked around using screen and bittornado, I believe want to do what hymn for life was doing. Which is spawn a bittorrent process via SSH, be able to exit the SSH shell, and have the bittornado download continue in the background. So what i've done is using screen and putty.
1. ssh into box via putt
2. start screen
3. use btdownloadheadless.bittornado to start the download
4. now I exit putty
5. I login via VNC and I can see that the process is still running in the back ground, great!

now my question...

6. How do i check the status of the download I spawned via the [now closed] SSH session? I'd like to be able to check in on it so see what % is done, and when it will finish. I couldn't find any documention about checking the status of an existing process.

~ego

---

### Post by scxtt on 2007-06-28
you use screen as follows:

screen <command you want to run>
ex. **screen bittorrent-curses name_of_torrent.torrent**
which would start, for example, PID 12345

to reconnect,

screen -r <PID from above>
ex. **screen -r 12345**

if you do a **ps -ef** you'd see something like: *SCREEN bittorrent-curses name_of_torrent.torrent*

using CTRL+A then CTRL+D you can detach the screen anytime ...

i've even wrote a little function to tell me all my active screens and i just pick which one i want to connect to ,,,

---

### Post by bodhi.zazen on 2007-06-28
+1 screen \o/

Have you looked at rtorrent ?

[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

---

### Post by theonlyalterego on 2007-06-28
> **bodhi.zazen said:**
> +1 screen \o/

Have you looked at rtorrent ?

[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

thanks for the quick responses, rtorrent looks like it will fulfill all my needs and a few more :) that howto is awesome! I'm pretty much setup using the situation described in the howto anyway, I'm downloading mp3 torrents, upon finishing I seed for a bit then move them into my gnump3d directory =) with the power of rtorrent I should be able to streamline that process significantly! ::happy::

Thanks again :)

---

### Post by raoul on 2007-07-06
rtorrent is a great bittorrent client. I've been using it for the last 6 months and I am happy with it.

I thought you might be interested in trying a simple [rtorrent web frontend]("http://www.g-loaded.eu/2007/06/23/rtorstat-a-simple-rtorrent-status-web-page-generator/"). It creates a simple html page with the status of your torrents.

my 2 bits

---

### Post by djhworld on 2007-07-08
Hi there, I'm a fellow rtorrent fan!

The coolest thing about it, is you can set it up to "watch" a folder for changes, so when you download a .torrent, download it to your "watched" folder and it'll start the torrent automatically!

I've set it up using screen as well, running in daemon mode under a bash alias

```

alias startrt="screen -dmS torrentit rtorrent" #start a screen session called "torrentit" running rotrrent
alias getrt="screen -r torrentit" # reattach to rtorrent screen session

```

So basically, I just do a quick "startrt" and rtorrent starts silently in the background. 

If I want to check up on it, I just reattach, then detach using Ctrl-a and D.

---

### Post by theonlyalterego on 2007-07-10
Thanks for the replies! I like web frontend =) 
Just gonna have to tweak it to include some simple authentication.

Thanks for the quick bash alias's those are a great idea.

---

### Post by dimeotane on 2007-08-07
the downside to rtorrent is that it has no UPnP support yet.  So I can hardly get it to download a thing with my home network setup.

Any other command line torrent downloading programs that support UPnP?

---

### Post by brdoco on 2007-08-22
when running rtorrent in screen, i can't ctrl-s to start a torrent.  its like the ctrl-functions aren't making it past screen to rtorrent.

help?

---

### Post by p-stone on 2007-08-23
I've been scouring the internet trying to find what you put in your rtorrent.rc to have it automatically start the torrents it adds. I'll set up queuing or something so I don't bog myself down but the reason I want to use rtorrent is to make downloading as transparent as possible. Ideally I'll save a torrent to a specified directory, rtorrent will see it, load it and start it and when it's finished move it to a new directory. I've found a way to do everything online except for the auto starting part, any ideas?

Thanks

---

### Post by brdoco on 2007-08-24
go to the link posted above for the walk thru.  what you're describing is the watch folder, and is defined in the config file.

as for it automatically moving a file once the download is complete.. i don't think it can do that.

---

### Post by p-stone on 2007-08-24
brdoco-

I have a watch directory set up:
```

schedule = watch_directory,10,10,load_start=/home/cornucrapia/storage/downloads/*.torrent
schedule = tied_directory,10,10,start_tied=
schedule = untied_directory,10,10,close_untied=

```
which does add the torrents automatically, I was asking about something in addition to that to start them downloading without any input from me. If there isn't a way it's a limitation I can accept but it would be nice.*EDIT* this appears to have been a combination of a rogue torrent and my own impatience, torrents now get added and begin downloading exactly as I'd like*EDIT*

As for the moving completed files there appears to be a way to do this although I can't seem to get it going 
[the config is here]("http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#Movecompletedtorrents") (you have to upgrade your rtorrent for it to work, at least from the one in the repos right now)
Unfortunately as I said it's not working for me. Here's my config:
```

on_finished = move_complete,"execute=mv,-u,$d.get_base_path=,/home/cornucrapia/storage/completeddownloads/;d.set_directory=/home/cornucrapia/storage/completeddownloads/"

```
tips, hints, requests for clarification and so on would be much appreciated

---

