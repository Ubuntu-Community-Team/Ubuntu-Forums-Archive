---
title: "CLI Gurus - can you help me with my tiny backup script?"
date: 2007-04-26
forum: General Help
---

### Post by kolinab on 2007-04-26
Hi,

Today I made my first attempt at creating a little backup script for some persona files.

I called it 'backupscript,' made it executable, and put it in my /home. I fiddled around and finally got it working the way I wanted it to. What I'm wondering though, is why I have to type:

```

bash backupscript

```

instead of just typing

```

backupscript

```

I can print the script here if you like, but I think the answer will probably be pretty simple . . . :) 

I did a little reading about .bash_profile and paths and stuff, but I got a little bogged down. The little script is working now so that's pleasing enough for now. Just wondering why you have to do the 'bash'

Thanks!

Kolin

---

### Post by dcstar on 2007-04-27
> **kolinab said:**
> Hi,

Today I made my first attempt at creating a little backup script for some persona files.

I called it 'backupscript,' made it executable, and put it in my /home. I fiddled around and finally got it working the way I wanted it to. What I'm wondering though, is why I have to type:

```

bash backupscript

```

instead of just typing

```

backupscript

```

I can print the script here if you like, but I think the answer will probably be pretty simple . . . :) 

I did a little reading about .bash_profile and paths and stuff, but I got a little bogged down. The little script is working now so that's pleasing enough for now. Just wondering why you have to do the 'bash'

Thanks!

Kolin

Executable programs have to exist in a Directory set by your "Path" variable, this is so Linux knows where to look when you type "bash" (or anything else).

"bash" is in one of these directories so it runs, your "backupscript" is not, so it doesn't.

Unlike DOS, the current directory you are in is not used to run commands (unless it happens to be one of the Path directories).

If you typed "./backupscript" it will run, because you are now supplying a direct reference to the file and not relying on a search of the Path variables to find it.

---

### Post by kolinab on 2007-04-27
David,

Thanks so much for this reply. It makes perfect sense the way you explain it. I was used to the way DOS behaved.

Cheers!!

Kolin

---

### Post by Skrynesaver on 2007-04-27
Further note on dcstar's answer, you can set your PATH environment variable to include a $HOME/bin, a sensible place to put your own scripts, this could be added at the end of your .bashrc
```

PATH=$PATH:$HOME/bin
```
And of course all the scripts in this directory should be executeable
```
chmod 755 scriptname.sh
```
On a side issue, when using backup you are better scheduling it to happen automatically, cron is the way to go for this one, schedule a back up @ 3am everymorning or whenever suits.
man 5 crontab
And then with that open for reference open another terminal and 
crontab -e
Welcome to the wonderful world of owning and controling your own computer ;)

---

### Post by anaconda on 2007-04-27
And if you prefer the DOS way you can also add ./ to your PATH.

So that the current directory will also be searched when you give commands.  Just think carefully do you want to put it to the beginning or to the end of your PATH.. 

ie. if you have a script named "ls" do you want to run it from the current directory or the systems ls -command..

---

### Post by kolinab on 2007-04-27
Wow, those two replies are both really helpful too. I'll be doing more work and learning on this this weekend - thanks for the help guys, it's fun to use the command line again and have it do what I want!

---

