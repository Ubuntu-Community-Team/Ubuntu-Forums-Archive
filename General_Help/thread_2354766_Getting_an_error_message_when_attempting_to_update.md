---
title: "Getting an error message when attempting to update ClamAV using the terminal"
date: 2017-03-06
forum: General Help
---

### Post by John_Patrick_Mason on 2017-03-06
After installing ClamAV using:

```
sudo apt-get install clamav
```

I'm getting an error message when I type:

```
sudo freshclam
```

that looks like this:

```

ERROR: /var/log/clamav/freshclam.log is locked by another process
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).

```

Any ideas?

---

### Post by Perfect Storm on 2017-03-06
Try:
```
sudo /etc/init.d/clamav-freshclam stop
```

---

### Post by John_Patrick_Mason on 2017-03-06
> **Artificial Intelligence said:**
> Try:
```
sudo /etc/init.d/clamav-freshclam stop
```

And then?: 

```
sudo freshclam
```

This is what I get for the output:

```

main.cvd is up to date (version: 57, sigs: 4218790, f-level: 60, builder: amishhammer)
daily.cvd is up to date (version: 23174, sigs: 1727979, f-level: 63, builder: neo)
bytecode.cvd is up to date (version: 290, sigs: 55, f-level: 63, builder: neo)

```

So I guess I'm go to go, right?

---

### Post by Perfect Storm on 2017-03-06
Aye

---

### Post by howefield on 2017-03-06
Check again in a little while, you should be on 23175..

```
Subject: [clamav-virusdb] Signatures Published daily - 23175
&#9474;
&#9474;ClamAV Signature Publishing Notice
&#9474;
&#9474;Datefile:       daily
&#9474;Version:        23175
&#9474;Publisher:      Alain Zidouemba
&#9474;New Sigs:       360
&#9474;Dropped Sigs:   0
&#9474;Ignored Sigs:   162
```

---

### Post by John_Patrick_Mason on 2017-03-06
And if I want to output the results to a file, can I do this?:

```

clamscan -r --bell -i / > ClamAV_log.txt

```

---

### Post by deadflowr on 2017-03-06
> **John_Patrick_Mason said:**
> And if I want to output the results to a file, can I do this?:

```

clamscan -r --bell -i / > ClamAV_log.txt

```

You can create log files, that will log whatever was outputted from clamscan for later review with the log option like
```
clamscan -r --bell -i / --log=Path/to/where/you/want/the/log/to/be/clamscan.log
```

---

### Post by John_Patrick_Mason on 2017-03-06
> **deadflowr said:**
> You can create log files, that will log whatever was outputted from clamscan for later review with the log option like
```
clamscan -r --bell -i / --log=Path/to/where/you/want/the/log/to/be/clamscan.log
```

Also, where is the Windows partition generally located at? I would much rather have ClamAV scan only the Windows partition than the entire HDD.

---

### Post by deadflowr on 2017-03-06
> **John_Patrick_Mason said:**
> Also, where is the Windows partition generally located at? I would much rather have ClamAV scan only the Windows partition than the entire HDD.

Within Ubuntu it's in the /media/username/ folder
(usually within the Label name of the Windows Machine or the UUID of the same)
All external media are mounted in that location, by default.
(external just means not part of Ubuntu's system, and can mean a system on the same hard drive but different partition. As well as usbs, dvds, et cetra)

---

### Post by John_Patrick_Mason on 2017-03-06
Thanks, I guess my issue is solved. Thanks to all who have contributed.

---

