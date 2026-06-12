---
title: "Accidently deleted source code for running script"
date: 2018-06-10
forum: General Help
---

### Post by zerobytez on 2018-06-10
Not sure this is where this goes but I have nowhere else to go

Recently, I've been working on a Discord Bot in the ruby scripting language. Whilst trying to back it up, I absentmindidly ran rm instead of cp. However, ruby is still running the script, and I have confirmed it is indeed still running and responding to input from the discord server. Is there any way I can recover the code? The script writes a lot to the hard drive, so it's most likely overwritten itself, and I don't want to risk it being lost forever with shutting it down.

---

### Post by dragonfly41 on 2018-06-10
Since you need a quick response with your session still running I did a quick search to find this ...

[https://serverfault.com/questions/863204/recover-a-running-script-from-a-terminal-session](https://serverfault.com/questions/863204/recover-a-running-script-from-a-terminal-session)

I'm not at all sure if it helps.   But I read this in above thread ..

rm[COLOR=#242729][FONT=Arial] and other tools [/FONT][/COLOR][I]unlink the file, removing the link from the file [I]name to the actual data (referenced by inode), but as long as a reference exists (hard link or open handle) the inode is not deleted.

[/I][/I]...

And here is another related thread  ...

[https://askubuntu.com/questions/6698/can-files-directories-deleted-with-rm-be-restored](https://askubuntu.com/questions/6698/can-files-directories-deleted-with-rm-be-restored)

The trash-cli idea seems useful, but first you need to reverse your rm.

...

Finally this thread discusses extundelete

[http://extundelete.sourceforge.net/](http://extundelete.sourceforge.net/)

Read the section .. [h=1][SIZE=2][FONT=arial]**What to do if you've deleted a file (or multiple files)**[/FONT][/SIZE][/h]...

You are correct to keep your computer session going but make sure that you don't overwrite the removed file.

---

### Post by zerobytez on 2018-06-11
The file has been overwritten due to the script writing to file, unfortunately, and the /proc/PID/fd/ files all refuse to read by anything.

---

