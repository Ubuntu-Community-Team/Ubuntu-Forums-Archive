---
title: "Command line editor and auto-complete"
date: 2007-05-12
forum: General Help
---

### Post by sonic6567 on 2007-05-12
Hello,

I come from a UNIX environment.  I am very used to a POSIX ksh shell.
I cannot deal with bash (quite simply, the arrow key recall for command line editing is to similar to windows and that by itslef makes me sick. the whole idea is to get away from windows)
I need to replicate my ksh environment in Ubuntu linux.
I have chsh'ed to ksh, and pdksh as well as set -o'd to vi.  However, I cannot succesfully duplicate the features I require.

Can someone PLEASE help me.

I want vi as a command line editor with NO arrow key editing.
I want esc-esc to auto-complete file names.

So far I can get one or the other but not both.

Please help me.

Thanks

---

### Post by taurus on 2007-05-12
Maybe you need the vim-full package!

```
sudo aptitude update
sudo aptitude install vim-full
```

---

### Post by sonic6567 on 2007-05-12
I have installed vim-full as you suggested however i am getting the same results.
Am i missing some configuration somewhere? Something to enable vim-full perhaps?

Thank you

---

### Post by stylishpants on 2007-05-13
vim-full has nothing to do with this, if I understand you correctly.  You're talking not talking about being unhappy with the behaviour of the vi command.

You are talking about the editing mode keybindings of the ksh shell, which can be set to a vi-like mode or an emacs-like mode.  Is that correct?

From the ksh man page, it looks like you will have to define vi mode (set -o vi) and then remap some of the keys to do what you want.

To do that, you will need to do something like this:

```
# Use keyboard trap to map keys to other keys 
# note that escape sequences vary for different terminals so these 
# may not work for you 
trap '.sh.edchar=${keymap[${.sh.edchar}]:-${.sh.edchar}}' KEYBD 
keymap=( 
  [$'\eOD']=$'\eb'   # Ctrl-Left  -> move word left 
  [$'\eOC']=$'\ef'   # Ctrl-Right -> move word right 
  [$'\e[3~']=$'\cd'  # Delete     -> delete to right 
  [$'\e[1~']=$'\ca'  # Home       -> move to beginning of line 
  [$'\e[4~']=$'\ce'  # End        -> move to end of line 
) 
```

That excerpt is from "/usr/share/doc/ksh/example.kshrc".

You will need to determine the proper escape sequences for your system.  

Or you could use bash, which has the ["bind" command]("http://articles.techrepublic.com.com/5100-10877_11-5683375.html") to make it easier to do this sort of thing.  :)





> 
I cannot deal with bash (quite simply, the arrow key recall for command line editing is to similar to windows and that by itslef makes me sick. the whole idea is to get away from windows)


I can understand the need to stick with ksh over bash if that's your thing, but to hear bash called windows-like is kind of galling.  Bash has had this feature since before Windows existed.

Command history was introduced in csh in the 1979, but as far as I can tell, the use of the up arrow for history dates back to June 12, 1989, when somebody called "Chet Ramey" made this post:
[http://groups.google.com/group/gnu.bash.bug/browse_thread/thread/8e020a1550905807/1fc7b688f5d44438?lnk=gst&q=up+arrow+history&rnum=57#](http://groups.google.com/group/gnu.bash.bug/browse_thread/thread/8e020a1550905807/1fc7b688f5d44438?lnk=gst&q=up+arrow+history&rnum=57#)


Like most everything else in DOS, this feature was copied from UNIX but in a half-assed and inferior way.  Although the "cmd.exe" shell used in Windows now has command history with the up-arrow now, it did not get it until sometime in the mid 1990s.  I can remember using DOS before it had this feature, and I'm not even all that old.

---

### Post by sonic6567 on 2007-05-19
Whoa. Hang on. I am by no means implying that bash copied windows. We all know that windows has never had an original idea of their own.  Well.... except for when M$ said on CNN that it's new windows vista 'gadgets' are an innovation. (ha ha cough choke spit my drink out laughing)

I am a Unix (hpux in particular) admin. I am looking to duplicate that environment here as it is much more efficient than the default bash settings.

However, after everything I have tried, I seem to have come to the conclusion that something this simple is simply not possible.

But, if there is someone who can detail how to accomplish this, I will unofficially crown you supreme commander of all that is shell command key map editing.

At a shell command prompt, the arrow keys should not function. The editing mode should be vi. press esc to enter edit mode. press esc again to auto-complete and exit edit mode.

Thanks

---

