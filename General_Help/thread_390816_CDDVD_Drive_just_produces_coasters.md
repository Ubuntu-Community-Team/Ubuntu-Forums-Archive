---
title: "CD/DVD Drive just produces coasters"
date: 2007-03-22
forum: General Help
---

### Post by The-Wappy-One on 2007-03-22
Hi there and my first post here :)

Im now to Ubuntu and learning fast I've completely dropped windows and made the move.. Prompted more by widows going belly up on me and loosing a fair bit of data :(  but anyway i've tried to stay away from posting and instead opting for scowering the forms for help and on most things it has proved a great learning curv but my current problem has left me in a sticky jam
[b]
_The Problem_[/b]

No mater what CD/DVD burning program i use it gets half way throught and then i end up with a coaster :( i've so far wasted 12 of more disk's with trial and error trying to get this fixed.. and ithought i'd turn to here for help :)

**_The Error Log_**

```
imager (BraseroLocalImage) set_output
job (BraseroLocalImage) set_task
imager (BraseroLocalImage) get_track
job (BraseroLocalImage) set_task
Session starting:
	flags			= 16727 
	media type	= 0
	speed		= 6
	track type		= 8
	track format	= 2
	output		= none
job (BraseroGrowisofs) set_rate
recorder (BraseroGrowisofs) set_drive
recorder (BraseroGrowisofs) set_flags
job (BraseroGrowisofs) set_source
job (BraseroGrowisofs) set_task
recorder (BraseroGrowisofs) record
process (BraseroGrowisofs) getting varg
growisofs (BraseroGrowisofs) set_action
process (BraseroGrowisofs) got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-speed=6
	-dvd-compat
	-use-the-force-luke=tty
	-Z
	/dev/hdc=/home/wappy/Desktop/300.iso
process (BraseroGrowisofs) launching command
process (BraseroGrowisofs) stdout: Executing 'builtin_dd if=/home/wappy/Desktop/300.iso of=/dev/hdc obs=32k seek=0'
process (BraseroGrowisofs) stderr: /dev/hdc: engaging DVD-R DAO upon user request...
process (BraseroGrowisofs) stderr: /dev/hdc: reserving 2018234 blocks
process (BraseroGrowisofs) stderr: /dev/hdc: "Current Write Speed" is 6.1x1385KBps.
process (BraseroGrowisofs) stdout:      32768/4133343232 ( 0.0%) @0.0x, remaining 6306:55 RBU 100.0%
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_rate
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stdout:      32768/4133343232 ( 0.0%) @0.0x, remaining 14716:10 RBU 100.0%
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_rate
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stdout:      32768/4133343232 ( 0.0%) @0.0x, remaining 21023:06 RBU 100.0%
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_rate
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stdout:      32768/4133343232 ( 0.0%) @0.0x, remaining 27330:02 RBU 100.0%
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_rate
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stdout:      32768/4133343232 ( 0.0%) @0.0x, remaining 35739:16 RBU 100.0%
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_rate
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stdout:      32768/4133343232 ( 0.0%) @0.0x, remaining 42046:12 RBU 100.0%
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_rate
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr: :-[ WRITE@LBA=110h failed with SK=4h/ASC=08h/ACQ=03h]: Input/output error
process (BraseroGrowisofs) stderr: :-( write failed: Input/output error
job (BraseroGrowisofs) asked to stop
	status	= 1
	error		= 1
	message	= "Unhandled error, aborting"
iter (BraseroGrowisofs) stopping
process (BraseroGrowisofs) got killed
process (BraseroGrowisofs) stderr: :-( write failed: Input/output error/dev/hdc: flushing cache
growisofs (BraseroGrowisofs) set_progress
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_action
process (BraseroGrowisofs) stderr: EOF
iter (BraseroGrowisofs) stopped
job (BraseroGrowisofs) got out of loop
job (BraseroGrowisofs) set_task
Session error : Unhandled error, aborting

```



**_The Hardware_**

Lite-On SOHW-1673S


Any help would be appreciated :) i do have a temp solution .. send it over the network and use the wifes pc, but its only a temp solution she don't like me messing with her pc much unless its broke :)



Any help is appreciated and thanks in advance.


The-Wappy-One



P.s the drive has been tested on another pc (With Windows on not linux) and it works fine?

---

### Post by poohbear1616 on 2007-03-22
> process (BraseroGrowisofs) stderr: :-( write failed: Input/output error
job (BraseroGrowisofs) asked to stop
	status	= 1
	error		= 1
	message	= "Unhandled error, aborting"

Started getting that kind of message when my drive went bad.
But you said this.

> P.s the drive has been tested on another pc (With Windows on not linux) and it works fine?

So thats out.:confused: 

I use gnomebaker with a diff. model lite-on and it works great.

---

### Post by gestahl on 2007-03-23
same here , so far 2 coasters at 8x , 1 at 16x , and just now 1 at 6x , all happening at like 50%s >( anyone has any idea ?

---

### Post by rich86 on 2008-05-09
Sorry to bump up this thread. Did you find a solution? I am getting a very similar error:
```
...
...
...
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:    16384000/4470016000 ( 0.4%) @0.0x, remaining 208:24 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:    16384000/4470016000 ( 0.4%) @0.0x, remaining 226:31 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr: :-[ WRITE@LBA=1f40h failed with SK=3h/ASC=0Ch/ACQ=00h]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 1
	message	= "Unhandled error, aborting"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
BraseroGrowisofs stderr: /dev/scd0: flushing cache
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_set_current_action
Session error : Unhandled error, aborting (brasero_burn_record burn.c:2270)
```

So far made a few coasters and not one successful burn (trying both kb3 and Brasero. I managed to write the live cd for Hardy (from gutsy), but come to think of it that might have taken more than one attempt. I will admit not tried the drive in windows yet (i might have made the drive a bit small :-\"but i will try later).
I have an internal "DRW-3S163" on IDE as master with a dvd-rom as slave. At the moment they are only on a 40cable wire not a new 80, could that make a difference. Have tried 2 brands of dvd-r (all i have around at the moment).
Thanks in advance for any ideas. Sorry if i am hijacking this thread.

Richard

EDIT: i also tried making iso's then burning but that failed too.

---

### Post by dukemaru on 2008-06-15
exact same problem here.
Nothing I do works. I just get CD or DVD coasters.
This started with 8.04. NEVER had this problem prior to that.

---

### Post by dukemaru on 2008-06-21
Bump.

---

### Post by daitheflu08 on 2008-07-01
I don't know about you guys but the only reason I have that exact same error message is when I'm using BRAND NEW Maxxel DVD+R these discs are not as good quality as say: imation DVD-Rs

I just ran one to try and burn a maxxel which failed.

Then without closing the program switched DVDs and tried the imation and it works fine!:D

---

### Post by daitheflu08 on 2008-07-01
Odd thing is, as soon as I said that one of my imation failed.  Think it was scratched or dirty-- not sure

---

