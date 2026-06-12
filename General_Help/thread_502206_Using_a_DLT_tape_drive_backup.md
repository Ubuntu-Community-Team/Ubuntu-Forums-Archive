---
title: "Using a DLT tape drive backup"
date: 2007-07-16
forum: General Help
---

### Post by self-defence on 2007-07-16
Hi,
I've got a server running Ubuntu Server 6.06 and a SCSI DLT tape device.
But I've never used one under linux before. I read somewhere that it is supposed to turn up under /dve/tape but under ubuntu it is something else like /dev/st0 or am I misunderstanding the whole thing.
How do I use the device to backup data form my raid array. Is there some software to be used?

Thanks for any and I do mean any help on how ti use it.

Best regards.

---

### Post by Maxtorm on 2007-07-16
First thing to do is install mt-st.  This will give you the device initialization and tape control commands:
```
sudo apt-get install mt-st
```You'll then need to modify the /etc/stinit.def file to reflect the specifications of your tape drive (there are some sample drives listed in the boilerplate stinit.def file that will install with mt-st -- I think).

Once you've got stinit.def configured, reinitialize the device using:
```
stinit
```Then you're off to the races.  You should be able to read from and write to the tape by pointing tar to the appropriate device.

You're right in that /dev/st0 is typically your first SCSI tape device.  There are suffices for different modes as defined in the stinit.def file, so no suffix = Mode 1, st0l is Mode 2, st0m is Mode 3, and st0a is Mode 4.  You can prefix any of them with n for "no rewind" (i.e. nst0, nst0l, etc.).  I have done everything using the base st0 and not had to use the other modes, so I can't tell you much more about them.

---

### Post by self-defence on 2007-07-17
Maxtorm -> thanks I think it's working since I get this:
```
# mt -f /dev/st0 status
SCSI 2 tape drive:
File number=-1, block number=-1, partition=0.
Tape block size 0 bytes. Density code 0x1b (DLT 35GB).
Soft error count since last status=0
General status bits on (10000):
 IM_REP_EN

```

But how do I backup the data. Do I just make a script that copies the conten ontu the tape drive?
```
#tar -cf backup.tar *
#cp backup.tar /dev/st0
#rm -f backup.tax
```

Thanks for the help and nice day :)

---

### Post by Maxtorm on 2007-07-17
Tar should be able to do the task all at once since its output can be pointed directly to the tape device. Someone can correct me if I'm wrong, but I'm fairly sure that tar -- Tape ARchive -- assumes that it is being pointed to a tape device; the "-f" switch tells tar "go to file rather than a tape device."  I must admit, I'm still in the novice stages of getting my own DLT running correctly, but I *believe* you can do something like:
```
tar -c /dev/st0/backup.tar *
```

---

### Post by self-defence on 2007-07-17
Cool so tar is the answer. I never knew that so thank you Maxtorm.
I'm just trying it now.
The restore should work the same way right?

Thanks for the help again.

---

### Post by self-defence on 2007-07-18
Maxtorm -> it seems to be working

I used:
```
tar -cpf /dev/st0 db.sql
```
to backup the data

and
```
tar -dvf /dev/st0 db.sql
```
to check if backup was made

and
```
tar -xvf /dev/st0
```
to restore the data.

Now I just have to figure out how to make more than one backup on the tape.
I probably have to rewind and forward to get the right track number and then FF to that one and extract.
Can I get the number of tracks on the tape?

Thanks again Maxtorm and TAR does means Tape ARchive format. :)

Best of luck to you and thanks again

---

### Post by Maxtorm on 2007-07-18
According to this page [http://www.mkssoftware.com/docs/man1/mt.1.asp](http://www.mkssoftware.com/docs/man1/mt.1.asp) , you should be able to use
```
mt -f /dev/st0 eom
```
to space to the end of the existing data; however the man page for mt (at least the version from the repos) does not show that command.  Instead, it shows **eod**.  Not sure if that is a synonymous command?

Also, tar has an **--append** prefix, but again, I haven't tried it.  Let me know how you make out.  Good luck.

---

### Post by shirsch on 2007-08-31
Yes, you want the 'eod' command.

Be sure it targets the non-rewinding device, though, e.g.:

$ mt-st -f /dev/nst0 eod

When the tape stops, you should be able to initiate a new backup.

While we're on the subject of DLT tape drives, can anyone explain why I would see absolutely zero compression on a DLT7000?  I'm simply backing up a running Linux system with large amounts of source code (compressible text) on line also.  It invariably runs out of space at 34.9 GB, even though compression is engaged and I'm using a DLT IV tape.  I don't necessarily expect to see 2:1, but 0.98:1 is a startling result.

I've mucked endlessly with block sizes and every other st parm that could conceivably affect the situation.  The drive runs in streaming mode for > 98% of the time (no shoe-shining).

Is there a well-known issue of any sort with DLT7000 compression that I should be aware of?  I've tried two different units (both Compaq OEM pulls, FWIW).  Same results.

---

### Post by Maxtorm on 2007-08-31
This is going to sound like a stupid question, but are the compression flags set correctly for the mode you are using in the stinit.def file?

---

### Post by HiFiJive on 2007-11-27
I found the following link very useful when using tar to backup to tape. There are great examples and good weekly backup routine. 

URL to original help docs [http://www.faqs.org/docs/securing/chap29sec305.html]("http://www.faqs.org/docs/securing/chap29sec305.html")

[I]"..To move to the / root directory, use the command:

[root@deep]# cd /

It is important to always start with a full backup; say on a Friday, for example:

Friday 1. use tape 1 for the first full backup.

[root@deep] /# cd /
[root@deep] /# tar cpf /dev/st0 --label=" full-backup created on `date '+%d-%B-%Y'`." \
     	 --directory / home

Monday. use tapes 2 for the incremental backups.

[root@deep] /# cd /
[root@deep] /# tar cpNf /dev/st0 --label=" full-backup created on `date '+%d-%B-%Y'`." \
     	 --directory / home

Tuesday. use tapes 3 for the incremental backups.

[root@deep] /# cd /
[root@deep] /# tar cpNf /dev/st0 --label=" full-backup created on `date '+%d-%B-%Y'`." \
     	 --directory / home

Wednesday. use tapes 4 for the incremental backups.

[root@deep] /# cd /
[root@deep] /# tar cpNf /dev/st0 --label=" full-backup created on `date '+%d-%B-%Y'`." \
     	 --directory / home

Thursday. use tapes 5 for the incremental backups.

[root@deep] /# cd /
[root@deep] /# tar cpNf /dev/st0 --label=" full-backup created on `date '+%d-%B-%Y'`." \
     	 --directory / home

Friday 2. use tape 6 for the new full backups.

[root@deep] /# cd /
[root@deep] /# tar  cpf /dev/st0 --label=" full-backup created on `date '+%d-%B-%Y'`." \
     	 --directory / home
..."[/I]

Hope this helps.

---

### Post by JohnnyXmas on 2008-03-31
Hey guys,

Nice, concise thread, and I've got a question to add:

I work in an area where I need to test large amounts of DLT drives on a daily basis (as many as possible). These drives are of varying manufacture, compression method, etc, but all SCSI, and all manufactured less than a year ago. Right now we're testing them in Windows, which you can imagine is quite iffy and annoying. I'm trying to switch this process over to Linux, which is where I do everything else. Everything works just fine, but its equally annoying to have to constantly edit the config file every single time I hook up a new drive. Is there a base mode / compression method / etc that will work with most drives? All I have to do is perform a small read  / write verification, then rewind and eject the tape. So if the answer is "yes," I can write a quick script and go back to sleeping under my desk.

Thanks in advance!

---

