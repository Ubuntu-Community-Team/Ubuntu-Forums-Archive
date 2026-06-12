---
title: "Jingles in XMMS"
date: 2006-12-12
forum: General Help
---

### Post by Jorik90 on 2006-12-12
Hello,

I'm trying to let XMMS after every 10 songs play a specefic song. The easiest way to do this, is by inserting after ten songs the jingle (the specific snog) in the playlist. But.. I'm using the shuffle function, so this is not an option.
A queue function should do the job fine, but I don't know how to run this by command line (using cron jobs, so the song is in the queue every 10 minutes, or so). It doesn't have to use this, as long as it works!

Does anyone know such a program? I hope so.

Many thanks!

---

### Post by Jorik90 on 2006-12-13
Does no one know how to do this? Another program with at least the functions: shuffle, send a message to webserver when song changes (or run a command), playlist and the jingle function will do the job fine. Anyone?

---

### Post by stylishpants on 2006-12-13
> **Jorik90 said:**
> Does no one know how to do this? Another program with at least the functions: shuffle, send a message to webserver when song changes (or run a command), playlist and the jingle function will do the job fine. Anyone?

Read the xmms man page, or see the xmms help options.  You should always check these things first before posting a question like "how do I do X with program Y."

yojimbo@bobtail:~$ xmms --help
Usage: xmms [options] [files] ...

Options:
--------

  -h, --help                    Display this text and exit.
  -n, --session                 Select XMMS session (Default: 0)
  -r, --rew                     Skip backwards in playlist
  -p, --play                    Start playing current playlist
  -u, --pause                   Pause current song
  -s, --stop                    Stop current song
  -t, --play-pause              Pause if playing, play otherwise
  -f, --fwd                     Skip forward in playlist
  -e, --enqueue                 Don't clear the playlist
  -Q, --queue                   Add file(s) to playlist and queue

  -S, --toggle-shuffle[=SWITCH] Toggle the 'shuffle' flag.
  -R, --toggle-repeat[=SWITCH]  Toggle the 'repeat' flag.
  -A, --toggle-advance[=SWITCH] Toggle the 'no playlist advance' flag.

  SWITCH may be either 'on' or 'off'

  -m, --show-main-window        Show the main window.
  -i, --sm-client-id            Previous session ID
  -v, --version                 Print version number and exit.
  -q, --quit                    Close remote session.

Report bugs to [http://bugs.xmms.org](http://bugs.xmms.org)

---

### Post by hikaricore on 2006-12-13
> **stylishpants said:**
> Read the xmms man page, or see the xmms help options.  You should always check these things first before posting a question like "how do I do X with program Y."

yojimbo@bobtail:~$ xmms --help
Usage: xmms [options] [files] ...

Options:
--------

  -h, --help                    Display this text and exit.
  -n, --session                 Select XMMS session (Default: 0)
  -r, --rew                     Skip backwards in playlist
  -p, --play                    Start playing current playlist
  -u, --pause                   Pause current song
  -s, --stop                    Stop current song
  -t, --play-pause              Pause if playing, play otherwise
  -f, --fwd                     Skip forward in playlist
  -e, --enqueue                 Don't clear the playlist
  -Q, --queue                   Add file(s) to playlist and queue

  -S, --toggle-shuffle[=SWITCH] Toggle the 'shuffle' flag.
  -R, --toggle-repeat[=SWITCH]  Toggle the 'repeat' flag.
  -A, --toggle-advance[=SWITCH] Toggle the 'no playlist advance' flag.

  SWITCH may be either 'on' or 'off'

  -m, --show-main-window        Show the main window.
  -i, --sm-client-id            Previous session ID
  -v, --version                 Print version number and exit.
  -q, --quit                    Close remote session.

Report bugs to [http://bugs.xmms.org](http://bugs.xmms.org)

errmmmm how exactly does this help him?

---

### Post by stylishpants on 2006-12-13
> **hikaricore said:**
> errmmmm how exactly does this help him?

He said he wants to run the queue function from the command line.  There it is.

---

### Post by hikaricore on 2006-12-13
> **stylishpants said:**
> He said he wants to run the queue function from the command line.  There it is.

Ahh I misread part of the original post, I thought he was looking different software to control xmms's playlist..  sorry. :P

---

### Post by Jorik90 on 2006-12-23
It is now almost done.. but... when I use it, it works fine: butt.. I don't want the file twice in my playlist. I just use xmms -Q /music/jingle1.mp3, this adds the file to the playlist and queues it, ok, but if it is already present, it doesn't do anything with the old one. I want to remove older ones, or better, remove this song after something like 10 minutes (in case a very long song was just playing..) from the playlist. This is possible with xmms-shell, but I have to enter the number of the song in the playlist. Not a problem if a user is doing it, but it must be automatic. And the amount of numbers in the playlist will change now and then..

Is there a way to remove the file after it has been played? Or remove older (identical) files?

Many thanks :)

---

