---
title: "aMule, tempfolder larger then harddisk, how?"
date: 2007-04-18
forum: General Help
---

### Post by evaarties on 2007-04-18
I'm downloading a lot of files with aMule under Ubunte Edgy Eft and this is weird:

total size in temp folder is 64GB whilst my harddisk is only 40GB.. how can that be?

PS A lot of files are set to pause but still take up all space.

---

### Post by kidders on 2007-04-19
Hi there,

That's certainly odd! There *are* certain configurations that make this sort of thing possible, but if you had set such a thing up, you would know about it! I don't mean to be distrustful, but would you mind posting the output of the following...

```
du -Psh /tmp
df -h|grep /$
```

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by evaarties on 2007-04-20
I will do that tonight.

Btw, another user mentioned sparse files to me. Could be that that's the case here.

---

### Post by Hallvor on 2007-04-20
*deleted*

---

### Post by kidders on 2007-04-20
> **evaarties said:**
> I will do that tonight.

Btw, another user mentioned sparse files to me. Could be that that's the case here.

Depending on how you measure hard disk space consumption, you can often get different answers ... the use of sparse files is one reason this can happen because, depending on your point of view, the space necessary to store certain files may or may not be "used".

Another common reason for apparent inconsistencies is the storage of very large numbers of small files.

---

### Post by evaarties on 2007-04-21
> **kidders said:**
> Hi there,

That's certainly odd! There *are* certain configurations that make this sort of thing possible, but if you had set such a thing up, you would know about it! I don't mean to be distrustful, but would you mind posting the output of the following...

```
du -Psh /tmp
df -h|grep /$
```


ernst@ernst-desktop:~$ du -Psh /tmp
108K    /tmp
ernst@ernst-desktop:~$ df -h|grep /$
/dev/hda1              38G   23G   13G  64% /
ernst@ernst-desktop:~$ 



But I have to say that my /tmp is on it's own harddisk (20GB).. Why do you ask?? that Harddisk is old an only reliable for  a /tmp :D

---

### Post by kidders on 2007-04-21
Hey again,

I'm confused. :-( In your o/p you mentioned that the space available for temporary files is 40GB (rather than 20GB).

> **evaarties said:**
> I have to say that my /tmp is on it's own harddiskIf you're the kind of user that makes a lot of use of /tmp, that's a very good idea. :-)

---

### Post by evaarties on 2007-04-23
Well it's on its own harddisk because that harddisk is very unreliable.. 

Must say my tmp isn't that full.. how can I make it so Ubuntu makes more use of it ?


Could I make aMule use /tmp or does that conflict with the ubuntu tmp?

---

### Post by kidders on 2007-04-23
Oh I see... so it doesn't already do so? I presume you can ask it to if you'd like to ... it would be a bit strange if such a configuration option didn't exist.

> **evaarties said:**
> Well it's on its own harddisk because that harddisk is very unreliable.It isn't a good idea to use unreliable hard disks ... but I'm sure you know that hehe.

> **evaarties said:**
> Must say my tmp isn't that full.. how can I make it so Ubuntu makes more use of it ?Your system will use as much or as little temporary storage as it needs. I'm not sure what you're asking here. :-( Some applications are hungrier than others, when it comes to their use of temporary files. **Edit:** Something worth mentioning about /tmp is that very few file access restrictions tend to be imposed on what's in there ... so be careful what you use it for.

In answer to your original question, I'm guessing that sparse file storage accounts for the disk usage discrepancy, as you suggested. I was hoping to establish that from the output I asked you for, but I misunderstood your description of where you were keeping your files. Sorry.

The important thing to note though is that when a sparse file fills up, it will more than likely start *actually* consuming the space it sort of "theoretically" consumes at the moment ... so at some point, you might run out of disk space.

---

### Post by evaarties on 2007-04-23
> **kidders said:**
> Oh I see... so it doesn't already do so? I presume you can ask it to if you'd like to ... it would be a bit strange if such a configuration option didn't exist.

It isn't a good idea to use unreliable hard disks ... but I'm sure you know that hehe.

Your system will use as much or as little temporary storage as it needs. I'm not sure what you're asking here. :-( Some applications are hungrier than others, when it comes to their use of temporary files. **Edit:** Something worth mentioning about /tmp is that very few file access restrictions tend to be imposed on what's in there ... so be careful what you use it for.

In answer to your original question, I'm guessing that sparse file storage accounts for the disk usage discrepancy, as you suggested. I was hoping to establish that from the output I asked you for, but I misunderstood your description of where you were keeping your files. Sorry.

The important thing to note though is that when a sparse file fills up, it will more than likely start *actually* consuming the space it sort of "theoretically" consumes at the moment ... so at some point, you might run out of disk space.


I get it now :). 

About aMule: it has it's own tempfolder set to ~/.aMule/temp
In its settings I can change it to ie /tmp/aMule

Ernst

---

### Post by kidders on 2007-04-23
> **evaarties said:**
> About aMule: it has it's own tempfolder set to ~/.aMule/temp
In its settings I can change it to ie /tmp/aMuleThanks for the info. The disadvantage to changing that setting is that it breaks a sort of unofficial rule that all user-specific data should be in your home directory. However, you can now make better use of all your hard disk space. :-)

All the best!

---

### Post by evaarties on 2007-04-23
True :)

Maybe there should be made a new implemention of /tmp where every user gets its own /tmp/~  :D.

---

### Post by kidders on 2007-04-23
> **evaarties said:**
> True :)

Maybe there should be made a new implemention of /tmp where every user gets its own /tmp/~  :D.If you'd like to do that, there's no reason not to. There are a few ways (all of them very easy) of implementing your idea.

As a simple example, you might like to try...```
mkdir /tmp/evaarties
chmod 700 !$
ln -s !$ ~/tmp
```That would give you a private temporary folder in your own home directory, accessible only by you, but using shared space in /tmp. (If you have more users, a **find** or a **for** would allow you to repeat the operation lots of times.)

In general terms, desktop installs with as much temporary storage as you have are quite rare. In fact, many distros store theirs in RAM (for speed), and don't even bother wasting disk space with it.

---

### Post by evaarties on 2007-05-16
> **kidders said:**
> If you'd like to do that, there's no reason not to. There are a few ways (all of them very easy) of implementing your idea.

As a simple example, you might like to try...```
mkdir /tmp/evaarties
chmod 700 !$
ln -s !$ ~/tmp
```That would give you a private temporary folder in your own home directory, accessible only by you, but using shared space in /tmp. (If you have more users, a **find** or a **for** would allow you to repeat the operation lots of times.)

In general terms, desktop installs with as much temporary storage as you have are quite rare. In fact, many distros store theirs in RAM (for speed), and don't even bother wasting disk space with it.

I just tried it and it works like a charm!

This is what I did exactly:

Create your own tmpfolder for aMule:
```

cd /tmp
mkdir /amule-evaarties

```
Remove the old aMule tmp folder:
```

cd /~/.aMule/Temp
rm *
cd ..
rmdir Temp

```
Create a symbolic link to /tmp/amule-evaarties:
```

cd /~/.aMule/
ln -s /tmp/amule-evaarties /Temp

```
Now start aMule and see if /tmp/amule-evaarties is being filled with data.

NB Already downloading stuff? Move it to /tmp/amule-evaarties before removing ~/.aMule/Temp!!

NB In Ubuntu the folder /tmp is cleaned at boot, edit the following file:

gksudo gedit /etc/init.d/bootclean

find this section:

```

	#
	# Wipe /tmp, excluding system files, but including lost+found
	#
	# If TMPTIME is set to 0, we do not use any ctime expression
	# at all, so we can also delete files with timestamps
	# in the future!
	#
	if [ "$TMPTIME" = 0 ] 
	then
		TEXPR=""
		DEXPR=""
	else
		TEXPR="-mtime +$TMPTIME -ctime +$TMPTIME -atime +$TMPTIME"
		DEXPR="-mtime +$TMPTIME -ctime +$TMPTIME"
	fi

	EXCEPT='! -name .
		! ( -path ./lost+found -uid 0 )
		! ( -path ./quota.user -uid 0 )
		! ( -path ./aquota.user -uid 0 )
		! ( -path ./quota.group -uid 0 )
		! ( -path ./aquota.group -uid 0 )
		! ( -path ./.journal -uid 0 )
		! ( -path ./.clean -uid 0 )
		! ( -path './...security*' -uid 0 )'

	mkflagfile /tmp/.clean || return 1

```

and add this line:

```

		! ( -path ./amule-ernst )

```

above

```

		! ( -path ./lost+found -uid 0 )

```

so it becomes:

```

	#
	# Wipe /tmp, excluding system files, but including lost+found
	#
	# If TMPTIME is set to 0, we do not use any ctime expression
	# at all, so we can also delete files with timestamps
	# in the future!
	#
	if [ "$TMPTIME" = 0 ] 
	then
		TEXPR=""
		DEXPR=""
	else
		TEXPR="-mtime +$TMPTIME -ctime +$TMPTIME -atime +$TMPTIME"
		DEXPR="-mtime +$TMPTIME -ctime +$TMPTIME"
	fi

	EXCEPT='! -name .
		! ( -path ./lost+found -uid 0 )
		! ( -path ./quota.user -uid 0 )
		! ( -path ./aquota.user -uid 0 )
		! ( -path ./quota.group -uid 0 )
		! ( -path ./aquota.group -uid 0 )
		! ( -path ./.journal -uid 0 )
		! ( -path ./.clean -uid 0 )
		! ( -path './...security*' -uid 0 )'

	mkflagfile /tmp/.clean || return 1

```

Good luck!

---

