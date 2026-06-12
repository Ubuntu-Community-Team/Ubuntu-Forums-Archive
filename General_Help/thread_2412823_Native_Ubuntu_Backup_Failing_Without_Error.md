---
title: "Native Ubuntu Backup Failing Without Error"
date: 2019-02-17
forum: General Help
---

### Post by muddpup64 on 2019-02-17
For the past month or so my system backups have been failing. What I find odd is that it will go through most of the processes needed for backup but then fail at the very end without ever displaying an error message. I have attached serveral screenshots of the senerio to, hopefully, help paint a better picture.

I have been holding out bringing this to the forums for, I thought given it's behavoir, a patch for this issue might come out later in an update. I was wrong. Futhermore, I have been periodically doing intense googling sessions to try and find another person with this issue and then solve it, but again, I have come up on empty.

Without an error code I do not know what else to do. Perhaps I could be pointed in the direction of where the deja dup log files are located?

I really appreciated any help that could be thrown my way and I thank you in advance.

I am running an updated version of 18.04.

-Matt G.

---

### Post by muddpup64 on 2019-02-17
I attached one more picture down below. It is the one I feel to be the most important.

---

### Post by muddpup64 on 2019-02-18
Bump

If I have posted this in the wrong place, please let me know.

---

### Post by muddpup64 on 2019-03-01
Bump

At the very least I could use a hint on where to look.

---

### Post by muddpup64 on 2019-03-19
bump

---

### Post by muddpup64 on 2019-03-19
I am seeing a lot of bug reports around the time that my backups started to fail. However, each bug is different and I have no idea how to compare my problem with theirs.

I think it is also very important to note that I beleive an update was the cause but as I have been saying, I have no idea how to produce an error report. The backup just stops working and displays no errors.

---

### Post by muddpup64 on 2019-03-20
I figured if no one would help me I could at least start a log of my journey.

I found the log and have pasted the error message below:

```
[COLOR=#333333][FONT=monospace]DUPLICITY: INFO 1[/FONT][/COLOR][COLOR=#333333][FONT=monospace]DUPLICITY: . GPG error detail: Traceback (innermost last):
DUPLICITY: . File "/usr/bin/duplicity", line 1555, in <module>
DUPLICITY: . with_tempdir(main)
DUPLICITY: . File "/usr/bin/duplicity", line 1541, in with_tempdir
DUPLICITY: . fn()
DUPLICITY: . File "/usr/bin/duplicity", line 1393, in main
DUPLICITY: . do_backup(action)
DUPLICITY: . File "/usr/bin/duplicity", line 1414, in do_backup
DUPLICITY: . sync_archive()
DUPLICITY: . File "/usr/bin/duplicity", line 1204, in sync_archive
DUPLICITY: . copy_to_local(fn)
DUPLICITY: . File "/usr/bin/duplicity", line 1150, in copy_to_local
DUPLICITY: . copy_raw(src_iter, tdp.name)
DUPLICITY: . File "/usr/bin/duplicity", line 1068, in copy_raw
DUPLICITY: . data = src_iter.next().data
DUPLICITY: . File "/usr/bin/duplicity", line 1132, in next
DUPLICITY: . self.fileobj.close()
DUPLICITY: . File "/usr/lib/python2.7/dist-packages/duplicity/dup_temp.py", line 227, in close
DUPLICITY: . assert not self.fileobj.close()
DUPLICITY: . File "/usr/lib/python2.7/dist-packages/duplicity/gpg.py", line 305, in close
DUPLICITY: . self.gpg_failed()
DUPLICITY: . File "/usr/lib/python2.7/dist-packages/duplicity/gpg.py", line 272, in gpg_failed
DUPLICITY: . raise GPGError(msg)
DUPLICITY: . GPGError: GPG Failed, see log below:
DUPLICITY: . ===== Begin GnuPG log =====
DUPLICITY: . gpg: WARNING: "--no-use-agent" is an obsolete option - it has no effect
DUPLICITY: . gpg: AES256 encrypted data
DUPLICITY: . gpg: encrypted with 1 passphrase
DUPLICITY: . gpg: decryption failed: Bad session key
DUPLICITY: . ===== End GnuPG log =====
DUPLICITY: .
DUPLICITY: .[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]DUPLICITY: ERROR 31 GPGError
DUPLICITY: . GPGError: GPG Failed, see log below:
DUPLICITY: . ===== Begin GnuPG log =====
DUPLICITY: . gpg: WARNING: "--no-use-agent" is an obsolete option - it has no effect
DUPLICITY: . gpg: AES256 encrypted data
DUPLICITY: . gpg: encrypted with 1 passphrase
DUPLICITY: . gpg: decryption failed: Bad session key
DUPLICITY: . ===== End GnuPG log =====
DUPLICITY: .[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Duplicity version: 0.7.17
Python version: 2.7.15rc1
[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]OS Distro and version: Ubuntu 18.04[/FONT][/COLOR]
```


I have also started a bug report at this address: [https://bugs.launchpad.net/duplicity/+bug/1820963](https://bugs.launchpad.net/duplicity/+bug/1820963)

---

