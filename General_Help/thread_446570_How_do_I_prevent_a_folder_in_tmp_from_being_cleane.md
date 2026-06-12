---
title: "How do I prevent a folder in /tmp from being cleaned at boot"
date: 2007-05-17
forum: General Help
---

### Post by evaarties on 2007-05-17
In my /tmp I created a folder which I need to stay there after rebooting Ubuntu (7.04).

I managed to edit /etc/init.d/bootclean so the folder stays but the contents are still gone after a reboot.

What must I edit more? Or can I place a file in the folder so it won't be cleaned (I read something about a .clean file but that doesn't work)?

In detail:

I created the folder

```

/tmp/amule-ernst

```

afterwards I edited bootclean

```

gksudo gedit /etc/init.d/bootclean

```

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
		! ( -path ./amule-ernst )
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

But this only prevents the created folder from being removed.

---

### Post by bernied on 2007-05-17
This seems a lot of effort.
Can you not just tell whatever application it is to put the file somewhere else?

---

### Post by Rinzwind on 2007-05-17
Why don't you use /usr/tmp/?

---

### Post by yota on 2007-05-17
Probably the right place should be /var/tmp, quoting from [http://www.pathname.com/fhs/2.2/fhs-5.15.html](http://www.pathname.com/fhs/2.2/fhs-5.15.html)
> 
/var/tmp : Temporary files preserved between system reboots


/usr should be mountable read-only and so is not suited to store variable data.

---

### Post by evaarties on 2007-05-17
Great tips, infact the application (aMule) has it's own temp folder in ~/.aMule/Temp.

The reason I want to place that folder on /tmp is that /tmp resides on a harddisk which is 20Gb in size.

aMule can easily make use of the free space on /tmp.

So I hope someone can offer the solution for my question.

---

### Post by yota on 2007-05-18
You can use 'mount --bind'

> 
  mount --bind olddir newdir
       After this call the same contents is accessible in two places.  One can
       also remount a single file (on a single file).


for instance let's say that your 20GB hd is /dev/sdx1
[LIST=1]
[*]mount dev/sdx1 /mnt/tmp
[*]mkdir /mnt/tmp/var-tmp /mnt/tmp/slash-tmp
[*]mount --bind /mnt/tmp/slash-tmp/ /tmp
[*]mount --bind /mnt/tmp/var-tmp/ /var/tmp
[/LIST]

now both tmp and var/tmp are redirected to the same disk and you can put amule's temp files on /var/tmp.
Otherwise you can use the same trick to make just ~/.aMule/temp go on the other disk.

Hope this helps!

p.s.
Sorry for not answering your question, IMHO the point is not how to keep things in a directory that by design is cleaned with no warning; instead we should try to place things on the best place, obiously what "best" means can be further discussed.

---

