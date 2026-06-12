---
title: "where to set functions to be available to ALL sh (dash) scripts - ditto for bash"
date: 2015-12-16
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2015-12-16
Where should I put a function so that it will be available to ALL sh (i.e. dash) scripts, not just interactive ones, for both root and regular users?

Same question for bash.

-------------------------------------------------------------------------------
Trusty. 32 bit. Lightdm. Openbox only, no other DE per se.

---

### Post by ian-weisser on 2015-12-16
Look at $PATH
```
$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
```
I would likely put them in /usr/local/bin

---

### Post by Dreamer Fithp Apprentice on 2015-12-16
Thanks, General Wallace, er Weisser.

But that is a directory. I suppose I could put there a script or sourcable code that could be invoked to CREATE a function or set of functions as needed. But what I'm looking for is one or more config files that would be loaded as early as possible automatically.

Something like
/etc/bash.bashrc
but that works for sh also or a separate one for sh.  Config files that get read early so that the functions will be available to all scripts, including non interactive ones, for root and regular users.

In the worst case I may have to settle for a file with sourcable code to establish functions, which I'd have to source explicitly in any script where I wanted them used, but I'd prefer a more elegant approach if possible.

---

### Post by SeijiSensei on 2015-12-16
Take a look at /etc/profile and see if that helps.

---

### Post by Dreamer Fithp Apprentice on 2015-12-16
Thank you, SeijiSensei.  I have experimented with that file already, but I didn't notice the commented header until now. It is very strange, it SAYS```
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).
```but IN FACT it seems to work for bash but not sh. Maybe only the default interactive shell  sources that file? ("Default interactive shell" may not be the right expression - I mean whatever shell is used after login for scripts without a shebang, whatever a terminal emulator uses by default.) I can force sh running in a terminal to source it with```
. /etc/profile
```and it DOES load a function from there when I do that so bash-centric syntax isn't the problem. But that goes away of course, when I close that terminal.

---

### Post by steeldriver on 2015-12-16
I don't think dash has a *default* initialization file for non-login shells - compare the FILES section of 'man dash' to that in 'man bash'

.profile is only read for login shells afaik

You may find this helpful: [http://askubuntu.com/questions/86139/what-is-the-dash-equivalent-for-bashrc](http://askubuntu.com/questions/86139/what-is-the-dash-equivalent-for-bashrc)

---

### Post by SeijiSensei on 2015-12-16
/bin/sh is just a symlink to /bin/dash. I have no idea what dash supports since I never use it.  You could try repointing /bin/sh to /bin/bash so you just have one shell like on Redhat-flavored distros.

---

### Post by Dreamer Fithp Apprentice on 2015-12-16
Thanks, Steeldriver. Indeed, that is helpful. It doesn't do the trick, but it advances my understanding and may prove useful in its own right. 

By experimentation I determined that:
I can set variables in /etc/profile and they will be seen by both bash in a terminal and dash in a terminal, and I guess at least some scripts.  Functions set there are only available to bash. The variable ENV is seen by both bash and dash but apparently only dash cares about it. So now I have one file where I can set bash specific functions and another file where I can set dash specific functions. Presumably I could source a third file in each of those 2 files and it could contain functions available to both bash and dash. So far, so good. 

But unfortunately most of the scripts I want to use my own functions in apparently aren't run by "login shells", which is a concept I haven't found a clear definition of yet.  Most of them are started, one by another in 3 chains. One chain of scripts starts in /etc/rc.local, one is started by the lightdm-gtk-greeter as a result of a setting in /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf, and another starts in ~/.config/openbox/autostart.sh. Only the scripts in the third group, starting with autostart.sh see any of these functions set in either file.

It may be there simply isn't any facility for this. If not, a less elegant way to do it would be to source a file with function definitions in the first script of each chain, and then, if it is possible, "export" the functions to the child scripts like you export a variable. That's if it can be exported once in the first script and get propagated to all descendants. If it has to be re-exported at each step, I might as well just source a function declaration file in each script.I haven't yet tried to see if the export approach is possible because I haven't yet given up on the idea that there may be some place (like /etc/init/ maybe) I can put a config file that will do the trick, if I knew the magic path/filename.

-------------------------

Thanks, SeijiSensei. Well, maybe, But I doubt that would achieve the intent, since the problem seems to be related to "login" vs. "non-login" scripts. I would also wonder if that wouldn't break a lot of the scripts that boot the system and are intended to run under dash, or at least slow boot down a lot. It might work. Heck I might even try it sometime in the spirit of experimentation, but it seems a little like using an axe when I'm looking for a scalpel to replace my bowie knife.  Sourcing my functions in each script, inelegant though it is, would be a lot less radical.

----------------------------

BTW, a curious fact:
~/.config/openbox/autostart.sh is run by sh, not bash, no matter what kind of shebang it has. Which make me wonder how it is invoked. Maybe it is sourced.

---

