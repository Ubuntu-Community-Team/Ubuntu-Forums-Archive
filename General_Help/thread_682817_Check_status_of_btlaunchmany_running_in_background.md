---
title: "Check status of btlaunchmany running in background"
date: 2008-01-30
forum: General Help
---

### Post by Slippy Lane on 2008-01-30
Hey, I like to think of myself as an "advanced novice" but I still need leading by the hand through some things!

Wanting to download torrents in the background on a remote machine, I followed some advice I found here at ubuntuforums and, from within an SSH to the machine in question, executed the command (btlaunchmany ~/torrents/&), then exited the SSH shell.

The download is now running quite happily on the other machine, but I have a couple of issues:

How can I check the status of the downloads running in the background? Do I need to take ownership of the process somehow?

If I kill the process and run the (btlaunchmany ~/torrents/&) command again to restart it, will it resume the downloads from the last point, or restart them from the beginning?

The reason for the second question is as follows: If I can't get the output from the background process, I'll need to kill it and restart it, redirecting its output to a file, and I don't want to have to restart all my downloads from scratch, as the download has been running for a couple of days already.

Anything I do with this process needs to be done  through an SSH connection as the machine in question has no monitor or keyboard.

Any help anyone can give me with this would be greatly appreciated.

---

### Post by clauguia on 2008-02-12
I found this tutorial:

[http://mandrivausers.org/lofiversion/index.php/t17941.html](http://mandrivausers.org/lofiversion/index.php/t17941.html)

Basically it says to use the screen command as follows:

> 
screen btdownloadcurses.py --display_interval 5 http:/this_is_a_url/MyTestTorrent.torrent

You shouln't see any difference from running it without the screen command.
Now press "Ctrl-A" followed by "d": this is the magic key combination to detach btdownloadcurses.py from the current window: the program hasn't stopped, it simply stopped using the console or ssh window.

close your window or you ssh session. If you simply close the ssh or console window without detaching first, the detach operation still occurs automagically.

Now open a new console or ssh session.

Type screen -r this is the command to re-attach the detached screen to your current console: you now see you torrent download is still in progress and has been downloading "behind the scenes".

If you have started several torrents as detached screens, you can type screen -ls to list the detached screens available on your machine. Then type screen -d -r the_screen_name where the_screen_name is one of the names listed by the previous command that you want to re-attach.

There is much more to the screen command, so refer to its (huge) man page if you need more details. There are lots more magic key pressed than "Ctrl-A d", for example "Ctrl-A K" kills the current scren altogether. The key commands can also be remapped if you like.


It worked for me, but the magic didn't last untill the file was fully downloaded. I don't know why.

---

### Post by Slippy Lane on 2008-02-13
Ah, it's okay. It turns out the torrents I was downloading were dead anyway.

What I do now is (btlaunchmany mytorrents > myoutput&), but I will try the screen method you mentioned. I've not really used the screen command before, but I think it warrants some reading of the man pages, as it looks like a very useful tool!

Thanks for the help

---

