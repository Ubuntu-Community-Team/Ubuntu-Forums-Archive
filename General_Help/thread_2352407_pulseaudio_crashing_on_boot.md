---
title: "pulseaudio crashing on boot"
date: 2017-02-12
forum: General Help
---

### Post by bblaha on 2017-02-12
My pulseaudio started failing regularly a couple of weeks ago. First this could mostly be solved by rebooting. Now it can't be solved at all.
I posted a question on AskUbuntu ( [http://askubuntu.com/questions/879037/pavucontrol-stuck-at-establishing-connection-to-pulseaudio-please-wait?noredirect=1#comment1367972_879037](http://askubuntu.com/questions/879037/pavucontrol-stuck-at-establishing-connection-to-pulseaudio-please-wait?noredirect=1#comment1367972_879037) ) but I think by what I found out today this is mostly irrelevant.

Today I tried a couple of things and found out I could solve the problem simply by starting pulseaudio manually ( pulseaudio --start ). My conlcusion was it doesn't autostart as it should. But why was it working earlier then? Only thing I could think of was it crashes on boot. I looked up how to create logs and did so. And indeed from what I could read from it it starts shutting down at line 1649 of the log file.

The logfile is too big to upload here, so I created a pastebin: [http://pastebin.com/tdmShs5V](http://pastebin.com/tdmShs5V)

Why is pulseaudio crashing on boot? Or is it, actually? How do I fix this?

Thanks in advance!

---

### Post by TheFu on 2017-02-12
I have the same issue. Except it dies whenever the input source program changes.  If vlc is playing, then stopped and then chromium tries to play audio, it is dead.  My easy solution, which is still a hassle, is to kill off pulse and restart it using a script between changing input sources. Drop this into a file, make it executable and run it before starting any program with sound output.  ALSA was harder to setup, but it "just worked" all the time after that.  In fact, pulse uses ALSA for output on many flavors of Ubuntu.

```
pulseaudio -k # kill a daemon
pulseaudio -D # restart the pulse daemon
amixer sset Master on

```

---

### Post by bblaha on 2017-02-12
Hi TheFu,
thank you for your reply.
So you just installed ALSA to solve this problem, did I get this right?

---

### Post by bblaha on 2017-02-20
I solved it:
sleep 5;pulseaudio --start is now a startup application. I feel a bit dirty now :(

---

