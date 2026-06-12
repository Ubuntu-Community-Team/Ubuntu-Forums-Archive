---
title: "bash scripts and aliasing help please?"
date: 2020-10-17
forum: General Help
---

### Post by jebi on 2020-10-17
Hi,
 
Could anyone tell me what is the correct locations to store your own bash scripts?
 
Etc/bin
Etc/sbin
 
?
 
Is there a difference if you want the script to be used system wide? or say all sudo enabled accounts? or just your own account?
 
Or if it needs to be run as sudo?
 
If I wanted to use a bash alias in bashrc how could I just use the script name?
 
Or would I have to do
 
alias runthis="sudo /usr/whatever/.scriptname”
 
is it the same for all debian based lx’s? what about centos, or arched based?
 
thx

---

### Post by &amp;KyT$0P# on 2020-10-17
> **jebi said:**
> Hi,
 
Could anyone tell me what is the correct locations to store your own bash scripts?

Usually [FONT=Courier New]$HOME/bin[/FONT], which is usually [FONT=Courier New]/home/[COLOR="#FF0000"]<you>[/COLOR]/bin[/FONT] where [COLOR="#FF0000"]<you>[/COLOR] is your username.

> Is there a difference if you want the script to be used system wide? 

Yes, then you would typically put it in [FONT=Courier New]/usr/local/bin[/FONT] .

> or say all sudo enabled accounts? 

That's a permissions question, not so much where you store the script.

> Or if it needs to be run as sudo?

This isn't either a question of where you store it.  If this is the case, your script should handle this.  For example, it could either abort if not sudo'd, or re-execute itself using sudo.

---

### Post by TheFu on 2020-10-17
halogen2, nicely stated.

[LIST]
[*]Personal scripts in ~/bin/
[*]System-wide scripts in /usr/local/bin/
[*]admin scripts that aren't sensitive in /usr/local/sbin/
[*]admin scripts with sensitive info inside /root/bin/
[/LIST]

Plus, nobody says this, but update the PATH as needed per account. Be careful about the order of directories.
Create any directories as needed, lock the permissions down as you see fit for your own ~/bin/

These are what long-time users setup, but you **can** do whatever you personally like.

All Unix systems, including android, can work this way. It isn't linux specific. I do the same on aix, solaris, hp-ux, irix, osx, digital unix, bsd, etc....

---

### Post by jebi on 2020-10-18
hi,

thx for the responses could i ask about the alias-ing in bashrc


[COLOR=#000000]alias runthis="sudo /usr/bin/.scriptname.sh"[/COLOR]


[COLOR=#000000]alias runthis="sudo /usr/bin/./scriptname.sh"

[/COLOR]which is right?

also im not 100% on PATH

do i need to change some file and add alias or .sh to some file?

thx

---

### Post by TheFu on 2020-10-18
Those two filenames are completely different.

I'm not a fan of having sudo hidden in a script or alias. I want to know when it is being used, so I don't accidentally type in my password without understanding why.  Imagine there's a nasty website out there that figures out how to use a mime-type to run local programs ... and they bury the sudo inside?  Now you may get prompted to enter a password, enter it, but not realize it was for a bad, bad, script, not something you intended. Don't forget that sudo usually has a 5-15 minute timeout too, before it asks for another password entry. This is configurable, of course, but if you have to ask how, perhaps it isn't a good idea to change that.

```
echo $PATH
```
Works exactly the same as on Windows, except, hopefully, ./ is not included like it does on Windows. HUGE security failure, IMHO.

---

### Post by dinkidonk on 2020-10-18
> **TheFu said:**
> 

[LIST]
[*]admin scripts with sensitive info inside /root/bin/ 
[/LIST]

Not sure what you mean by "sensitive info", but IMHO you should not put anything inside "/root/*". Scripts and executables only meant to be used by root should go into "/usr/sbin/" or "/usr/local/sbin/". If you do not want users to see the contents of the scripts, you can remove the "right to read" for all except root. Whenever I make a script which is only allowed to be run by root, the first lines would be:

```
if [ $USER != "root" ]; then
  sudo $0
  exit
fi
```

---

### Post by TheFu on 2020-10-18
That root check snippet has a few failure modes on some of my systems. 
I want a belt and suspenders for sensitive scripts, like those that have credentials.

But different admins do things differently.

---

### Post by dinkidonk on 2020-10-19
> **TheFu said:**
> That root check snippet has a few failure modes on some of my systems.

On Ubuntu my snippet should work OK, but for completion here are some other methods for root checks:

```
if [ $(id -u) -ne 0 ]...
if [ "$(whoami)" != "root" ]...
```

The first should work on most systems.

---

### Post by TheFu on 2020-10-19
For network backups, I use a root-equivalent account that allows just a few commands to be run, so any check of "root" will fail. Always check the uid ... the number -eq 0.

For backing up DBs, it is often easier to push the login credentials into the file performing the backups.  With that script under /root/, I know that some junior admin won't accidentally remove the permissions and make it world readable. That's my reasoning for that location.  I also store system config data in /root/backups/ to help with assorted issues that can happen, so /root/ is included in all backups anyway.  Just something I learned from my mentor in the 1990s. End user directories may not be available, but /root/ always is.  We used NFS with amd to mount user HOMEs on-demand.

Anyway, those are the reasons I can think of now, pre-caffiene.

---

