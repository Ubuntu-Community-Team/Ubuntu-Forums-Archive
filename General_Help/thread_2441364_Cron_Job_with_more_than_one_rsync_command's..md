---
title: "Cron Job with more than one rsync command's."
date: 2020-04-22
forum: General Help
---

### Post by Raymond Day on 2020-04-22
I got a 12TB hard drive to backup all my drives too. I want to run a rsync one time a week to back them up to it. But looks like I can't get it to work. I guess can't put more than one on a line.

Here is what my **/var/spool/cron/crontabs/root** file line looks like:

```
@weekly rsync -avP /media/4TB-Blue/ /media/12TB-backup/4TB-Blue && rsync -avP /media/PiDrive1TB/ /media/12TB-backup/PiDrive1TB && rsync -avP /media/VHS-videos/ /media/12TB-backup/VHS-videos && rsync -avP /media/WD-MyDrive-2TB/ /media/12TB-backup/WD-MyDrive-2TB && rsync -avP /media/1TB-WD/ /media/12TB-backup/1TB-WD && rsync -avP /media/500GB-Laptop-HDD/ /media/12TB-backup/500GB-Laptop-HDD #Backup 5 drives to a 12TB one
```

I have all ready backed it up using each of the commands one at a time on the command line so they do work.

Here is what I get when I run it.

```
Output from command rsync -avP /media/4TB-Blue/ /media/12TB-backup/4TB-Blue && rsync -avP /media/PiDrive1TB/ /media/12TB-backup/PiDrive1TB && rsync -avP /media/VHS-videos/ /media/12TB-backup/VHS-videos && rsync -avP /media/WD-MyDrive-2TB/ /media/12TB-backup/WD-MyDrive-2TB && rsync -avP /media/1TB-WD/ /media/12TB-backup/1TB-WD && rsync -avP /media/500GB-Laptop-HDD/ /media/12TB-backup/500GB-Laptop-HDD ..
sending incremental file list
rsync: opendir "/media/4TB-Blue/lost+found/#169083091" failed: Permission denied (13)
rsync: failed to set times on "/media/12TB-backup/4TB-Blue/lost+found/#163447252": Invalid argument (22)
rsync: failed to set times on "/media/12TB-backup/4TB-Blue/lost+found/#163447341": Invalid argument (22)
rsync: failed to set times on "/media/12TB-backup/4TB-Blue/lost+found/#163447411": Invalid argument (22)
rsync: failed to set times on "/media/12TB-backup/4TB-Blue/lost+found/#163447468": Invalid argument (22)
rsync: failed to set times on "/media/12TB-backup/4TB-Blue/lost+found/#169083309": Invalid argument (22)
rsync: failed to set times on "/media/12TB-backup/4TB-Blue/lost+found/#172097547": Invalid argument (22)
rsync: failed to set times on "/media/12TB-backup/4TB-Blue/lost+found/#172097664": Invalid argument (22)
rsync: send_files failed to open "/media/4TB-Blue/lost+found/#172097969": Device not a stream (60)

sent 47,212 bytes  received 1,087 bytes  96,598.00 bytes/sec
total size is 2,983,333,656,855  speedup is 61,768,021.22
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1196) [sender=3.1.2]
```

Did that in Webmin and it shows it like that.

Looked on Google for help and just can't find it good. So posting this here.

A uname -a show this:

**4.15.0-96-generic #97-Ubuntu SMP Wed Apr 1 03:25:46 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux**

I think my have to made a script to do this? If so how would that that script be?

Thank you.

-Raymond Day

---

### Post by Raymond Day on 2020-04-22
I just made a easy script and it seems to work now.

It looks like this:

```
#!/bin/bash
rsync -avP /media/4TB-Blue/ /media/12TB-backup/4TB-Blue 
rsync -avP /media/PiDrive1TB/ /media/12TB-backup/PiDrive1TB
rsync -avP /media/VHS-videos/ /media/12TB-backup/VHS-videos
rsync -avP /media/WD-MyDrive-2TB/ /media/12TB-backup/WD-MyDrive-2TB
rsync -avP /media/1TB-WD/ /media/12TB-backup/1TB-WD
rsync -avP /media/500GB-Laptop-HDD/ /media/12TB-backup/500GB-Laptop-HDD
```

I named it **backup-to-12TB.sh** and pointed the cron job to that file.

In Webmin when I run it now. It looks like this:

```
sending incremental file list
rsync: opendir "/media/4TB-Blue/lost+found/#169083091" failed: Permission denied (13)
rsync: failed to set times on "/media/12TB-backup/4TB-Blue/lost+found/#163447252": Invalid argument (22)
rsync: failed to set times on "/media/12TB-backup/4TB-Blue/lost+found/#163447341": Invalid argument (22)
rsync: failed to set times on "/media/12TB-backup/4TB-Blue/lost+found/#163447411": Invalid argument (22)
rsync: failed to set times on "/media/12TB-backup/4TB-Blue/lost+found/#163447468": Invalid argument (22)
rsync: failed to set times on "/media/12TB-backup/4TB-Blue/lost+found/#169083309": Invalid argument (22)
rsync: failed to set times on "/media/12TB-backup/4TB-Blue/lost+found/#172097547": Invalid argument (22)
rsync: failed to set times on "/media/12TB-backup/4TB-Blue/lost+found/#172097664": Invalid argument (22)
rsync: send_files failed to open "/media/4TB-Blue/lost+found/#172097969": Device not a stream (60)

sent 47,212 bytes  received 1,087 bytes  96,598.00 bytes/sec
total size is 2,983,333,656,855  speedup is 61,768,021.22
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1196) [sender=3.1.2]
sending incremental file list

sent 253 bytes  received 13 bytes  532.00 bytes/sec
total size is 984,249,588,543  speedup is 3,700,186,423.09
sending incremental file list
cannot delete non-empty directory: wordpress/wp-content/uploads/2008/07
could not make way for new regular file: wordpress/wp-content/uploads/2008/07
cannot delete non-empty directory: wordpress/wp-content/uploads/2008/08
could not make way for new regular file: wordpress/wp-content/uploads/2008/08

sent 3,216,653 bytes  received 42,874 bytes  2,173,018.00 bytes/sec
total size is 2,222,279,608,451  speedup is 681,779.78
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1196) [sender=3.1.2]
sending incremental file list

sent 408 bytes  received 15 bytes  846.00 bytes/sec
total size is 4,473,864,500  speedup is 10,576,511.82
sending incremental file list

sent 637 bytes  received 15 bytes  1,304.00 bytes/sec
total size is 12,856,461,155  speedup is 19,718,498.70
sending incremental file list

sent 17,008 bytes  received 39 bytes  34,094.00 bytes/sec
total size is 104,220,969,117  speedup is 6,113,742.54
```

Here is the command on the command line about the same as Webmin.

```
./backup-to-12TB.sh
sending incremental file list
rsync: opendir "/media/4TB-Blue/lost+found/#169083091" failed: Permission denied (13)
rsync: failed to set times on "/media/12TB-backup/4TB-Blue/lost+found/#163447252": Invalid argument (22)
rsync: failed to set times on "/media/12TB-backup/4TB-Blue/lost+found/#163447341": Invalid argument (22)
rsync: failed to set times on "/media/12TB-backup/4TB-Blue/lost+found/#163447411": Invalid argument (22)
rsync: failed to set times on "/media/12TB-backup/4TB-Blue/lost+found/#163447468": Invalid argument (22)
rsync: failed to set times on "/media/12TB-backup/4TB-Blue/lost+found/#169083309": Invalid argument (22)
rsync: failed to set times on "/media/12TB-backup/4TB-Blue/lost+found/#172097547": Invalid argument (22)
rsync: failed to set times on "/media/12TB-backup/4TB-Blue/lost+found/#172097664": Invalid argument (22)
rsync: send_files failed to open "/media/4TB-Blue/lost+found/#172097969": Device not a stream (60)

********************** Sophos Anti-Virus Alert ***********************
Error scanning file
"/media/4TB-Blue/lost+found/#172097969".

Access to the file has been denied

**********************************************************************

sent 47,212 bytes  received 1,087 bytes  32,199.33 bytes/sec
total size is 2,983,333,656,855  speedup is 61,768,021.22
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1196) [sender=3.1.2]
sending incremental file list

sent 253 bytes  received 13 bytes  532.00 bytes/sec
total size is 984,249,588,543  speedup is 3,700,186,423.09
sending incremental file list
cannot delete non-empty directory: wordpress/wp-content/uploads/2008/07
could not make way for new regular file: wordpress/wp-content/uploads/2008/07
cannot delete non-empty directory: wordpress/wp-content/uploads/2008/08
could not make way for new regular file: wordpress/wp-content/uploads/2008/08

sent 3,216,653 bytes  received 42,874 bytes  2,173,018.00 bytes/sec
total size is 2,222,279,608,451  speedup is 681,779.78
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1196) [sender=3.1.2]
sending incremental file list

sent 408 bytes  received 15 bytes  846.00 bytes/sec
total size is 4,473,864,500  speedup is 10,576,511.82
sending incremental file list

sent 637 bytes  received 15 bytes  1,304.00 bytes/sec
total size is 12,856,461,155  speedup is 19,718,498.70
sending incremental file list

sent 17,008 bytes  received 39 bytes  34,094.00 bytes/sec
total size is 104,220,969,117  speedup is 6,113,742.54
```

Is this good does it look like it will back it all up?

-Raymond Day

---

### Post by erind on 2020-04-23
Your first script was failing because you were chaining the rsync commands, the second runs only if the first succeeds (&&), and your first rsync was failing so the 2nd wouldn't run.  

The second script is better, however to speed things up and if your machine can handle it (plenty of RAM and fast drives with high disk IO), I'd recommend to run each rsync in the background or at least some of them, say three at a time, something like:

```
#!/bin/bash
rsync -avP /media/4TB-Blue/ /media/12TB-backup/4TB-Blue &
rsync -avP /media/PiDrive1TB/ /media/12TB-backup/PiDrive1TB &
rsync -avP /media/VHS-videos/ /media/12TB-backup/VHS-videos &
wait
rsync -avP /media/WD-MyDrive-2TB/ /media/12TB-backup/WD-MyDrive-2TB &
rsync -avP /media/1TB-WD/ /media/12TB-backup/1TB-WD &
rsync -avP /media/500GB-Laptop-HDD/ /media/12TB-backup/500GB-Laptop-HDD
```

As for the errors the rsync is failing because it's having issues with **lost+found **directory of the drive. I'd suggest to exclude it from the backup rsync command.

```

/media/12TB-backup/4TB-Blue/lost+found/#163447252": Invalid argument
```

After all the lost+found directory contains parts of corrupted files, not useful for backup. 
---

Excluding lost+found directory in your example would be like so:

```
rsync -avP --exclude 'lost+found' /media/4TB-Blue/ /media/12TB-backup/4TB-Blue
```

Note: Exclude path is always relative.

---

### Post by Raymond Day on 2020-04-23
Thank you erind that worked for the last+found but why can't I copy it?

I looked at it and it looks like this.

```
/media/4TB-Blue/lost+found# ls -l
total 30505812
brwxr-xr-x 1      561982500  218398983     4, 150 May  7  2020 '#163446803'
srwxr-xr-x 1      462160450 3828718052          0 Jun  4  1959 '#163446815'
crwxr-xr-x 1     1318275535 3010273909    31, 187 Nov 24  2412 '#163446858'
srwxr-xr-x 1     3403510747 1149097719          0 Feb 23  2056 '#163446903'
prwxr-xr-x 1     2073209973  991191857          0 May 10  1954 '#163446979'
srwxr-xr-x 1      214912921 4062729398          0 Sep  7  1977 '#163446987'
srwxr-xr-x 1     2370360703     757795          0 Jan  1  2218 '#163447145'
brwxr-xr-x 1     1936933337  413650902   164,  54 Sep 15  2057 '#163447161'
brwxr-xr-x 1       30149597 1836636717    33, 129 Aug 15  1905 '#163447252'
srwxr-xr-x 1      352599538 4255791844          0 Sep 13  2184 '#163447341'
prwxr-xr-x 1     2068505826 3569443708          0 Jun 22  2392 '#163447411'
crwxr-xr-x 1     1771106063  587829094   234, 202 Mar  5  1968 '#163447468'
srwxr-xr-x 1     4082797562 1241901337          0 Mar  6  2401 '#163447478'
prwxr-xr-x 1      455846107 2597797458          0 Apr 20  2384 '#163447481'
crwxr-xr-x 1      559616518 2166461445    81,   3 Sep  4  2105 '#169082938'
brwxr-xr-x 1     1619309703 1158024832   190,  52 Sep 14  2106 '#169082940'
prwxr-xr-x 1     2351055210 3639218128          0 Aug  5  2403 '#169082988'
crwxr-xr-x 1      690834113 1145745582   221,  85 May 27  2116 '#169082996'
prwxr-xr-x 1     2820387902 2566928389          0 Apr 18  2401 '#169083007'
crwxr-xr-x 1     2768396354  889193008   207,  53 Jul 10  2174 '#169083041'
srwxr-xr-x 1        7476736 2153857153          0 May 20  2018 '#169083043'
srwxr-xr-x 1      931178659 1577107584          0 Mar  3  2039 '#169083048'
drwxr-xr-x 2     2149233572   54534305       4096 Nov 17  2112 '#169083049'
prwxr-xr-x 1     1303618968  276957966          0 Oct 18  2381 '#169083060'
srwxr-xr-x 1         393544 3758609504          0 Apr 15  2242 '#169083071'
brwxr-xr-x 1      416309288 1519651458     1,  71 Jul 20  2021 '#169083072'
prwxr-xr-x 1     3790553527 2169241648          0 Jul 11  1911 '#169083076'
srwxr-xr-x 1      266401457   33071225          0 Jun 10  2153 '#169083079'
brwxr-xr-x 1     3095311440  515904541    94, 150 Nov  8  1975 '#169083082'
dr-s-wsrwT 2     1480476685 2631567745       4096 Sep  5  2134 '#169083091'
brwxr-xr-x 1     2818700721 3758309568     1,  71 Aug 14  1947 '#169083119'
crwxr-xr-x 1      259604572 3699403805    78,   0 Jan 29  2076 '#169083206'
brwxr-xr-x 1      810290299 3144385301   236,   0 May  2  2089 '#169083209'
crwxr-xr-x 1     3966444551 1879088876   112,   0 Sep 16  2434 '#169083222'
crwxr-xr-x 1     2693988656 1664795520    74,  26 Oct 11  2159 '#169083239'
--wS--Sr-- 1       79085352 3961470957      32768 Apr  5  2268 '#169083247'
brwxr-xr-x 1     3918921829  804546564     3, 232 Jul  9  2268 '#169083301'
brwxr-xr-x 1     2693115907 1143451648   163,   0 Jun  6  1902 '#169083309'
srwxr-xr-x 1     2214593594 1058075711          0 Oct 18  2193 '#169083314'
crwxr-xr-x 1     2571223593  405684243   208,  14 Feb  6  1917 '#169083316'
brwxr-xr-x 1     1686116544 2156008116   219, 129 Nov 29  2389 '#169083346'
prwxr-xr-x 1      615653978 2554140419          0 Oct 23  1936 '#169083353'
prwxr-xr-x 1      740437154 2294372008          0 Aug 31  2270 '#169083370'
drwxr-sr-x 2     3959368101  449132289       4096 Sep 10  2009 '#169083377'
srwxr-xr-x 1     1292507305 2919786532          0 Apr 26  2122 '#169083387'
crwxr-xr-x 1     2722292472  690660130     3,   3 May 12  2411 '#169083391'
---Sr-x--- 1     2496828555 1168384648      45056 Nov 14  2116 '#169083415'
brwxr-xr-x 1     3928834055 3163103662    45, 128 Jul  6  2444 '#169083430'
--wSr-x--- 1       21444235  436242568      49152 Jul  1  2278 '#169083433'
srwxr-xr-x 1     3187756099 2912629344          0 Aug 13  2243 '#172097540'
prwxr-xr-x 1     4167338270  409285987          0 Nov 27  1925 '#172097547'
prwxr-xr-x 1     2191479073  106076892          0 Aug  3  2041 '#172097555'
prwxr-xr-x 1      873739780  930217275          0 May 19  1923 '#172097664'
srwxr-xr-x 1     1205524595 2720727040          0 Nov 19  2011 '#172097668'
crwxr-xr-x 1     4227116362 2365751710   233, 135 Dec 16  2099 '#172097675'
brwxr-xr-x 1     3479765795 3943033646   190, 204 Jan 24  2387 '#172097679'
prwxr-xr-x 1      614673301 1232663313          0 Jun 15  2082 '#172097683'
srwxr-xr-x 1      572380700 1249176386          0 May 17  2079 '#172097732'
brwxr-xr-x 1     1656469064 3959565659    84, 240 Aug  4  1965 '#172097761'
prwxr-xr-x 1      489769249 3922484909          0 Aug 31  2005 '#172097765'
prwxr-xr-x 1     3972072202 3931751341          0 Jun 13  2252 '#172097779'
-rwxr-xr-x 1     2513663743 1804011061      40960 Mar 14  1948 '#172097969'
brwxr-xr-x 1      814219912 3519628556   195, 115 Aug 15  2302 '#172097983'
prwxr-xr-x 1     3459093958 2505148212          0 Oct 11  2186 '#172098034'
brwxr-xr-x 1      684814977 1960843518    67, 122 Jun 21  2212 '#172098036'
prwxr-xr-x 1     3639772523 3102168138          0 Oct  7  2226 '#172098039'
crwxr-xr-x 1     2522471960 1208440519    26,  71 Jan  4  2221 '#172098040'
prwxr-xr-x 1     2269863546 3280875832          0 Sep  8  1935 '#172098041'
-rwxr-xr-x 1 debian-deluged        126 2079220968 Apr 29  2018 '#196345926'
-rwxr-xr-x 1 debian-deluged        126  239820508 Apr 22  2018 '#196345928'
-rwxr-xr-x 1 debian-deluged        126  240395600 Apr 22  2018 '#196345931'
-rwxr-xr-x 1 debian-deluged        126 2139797200 May  6  2018 '#196345932'
-rwxr-xr-x 1 debian-deluged        126 2110536692 May 13  2018 '#196345933'
-rwxr-xr-x 1 debian-deluged        126 2079648480 May 20  2018 '#196345934'
-rwxr-xr-x 1 debian-deluged        126  270646116 May 31  2018 '#196345937'
-rwxr-xr-x 1 debian-deluged        126 1991820332 Jun  3  2018 '#196345941'
-rwxr-xr-x 1 debian-deluged        126 2083757784 Jun 10  2018 '#196345951'
-rwxr-xr-x 1 debian-deluged        126 2381491128 Apr  8  2018 '#196345955'
-rwxr-xr-x 1 debian-deluged        126 2229821752 Apr 18  2018 '#196345959'
drwxr-xr-x 2 debian-deluged        126       4096 May 31  2018 '#196345961'
-rwxr-xr-x 1 debian-deluged        126  240395600 Apr 22  2018 '#196345963'
-rwxr-xr-x 1 debian-deluged        126 2139797200 May  6  2018 '#196345964'
-rwxr-xr-x 1 debian-deluged        126 2079648480 May 20  2018 '#196345966'
drwxr-xr-x 2 debian-deluged        126       4096 May 28  2018 '#196345968'
-rwxr-xr-x 1 debian-deluged        126 1791500316 Aug 20  2018 '#196345973'
-rwxr-xr-x 1 debian-deluged        126 1985597908 Aug 20  2018 '#196345974'
-rwxr-xr-x 1 debian-deluged        126 1754319180 Aug 20  2018 '#196345975'
-rwxr-xr-x 1 debian-deluged        126 1864942516 Aug 22  2018 '#196345976'
-rwxr-xr-x 1 debian-deluged        126 1886735288 Aug 22  2018 '#196345978'
-rwxr-xr-x 1 debian-deluged        126 1783697188 Aug 24  2018 '#196345979'
-rwxr-xr-x 1 debian-deluged        126 1934346476 Aug 24  2018 '#196345981'
-rwxr-xr-x 1 debian-deluged        126 2140343152 Aug 26  2018 '#196345982'
-rwxr-xr-x 1 debian-deluged        126 1753060708 Aug 27  2018 '#196345983'
-rwxr-xr-x 1 debian-deluged        126 2007813304 Aug 27  2018 '#196345984'
crwxr-xr-x 1          12840      29742     0,   0 Feb  8  1987 '#196346005'
prwxr-xr-x 1     1535504476  687076786          0 May 15  2117 '#196346148'
-rwxr-xr-x 1 debian-deluged        126 1753545184 Aug 27  2018 '#196346161'
-rwxr-xr-x 1 debian-deluged        126 1767124612 Aug 29  2018 '#196346162'
-rwxr-xr-x 1 debian-deluged        126 2003868876 Aug 29  2018 '#196346163'
-rwxr-xr-x 1 debian-deluged        126 1873568332 Aug 31  2018 '#196346164'
-rwxr-xr-x 1 debian-deluged        126 1920011476 Aug 31  2018 '#196346165'
-rwxr-xr-x 1 debian-deluged        126 1366338504 Sep  3  2018 '#196346166'

```

Can I just delete all that and start it over? Or I guess I get:

```
/media/4TB-Blue/lost+found/#169083091# ls
ls: cannot open directory '.': Permission denied
```

I am root on there too.

Is the lost+found folder for fix errors I guess.

Did a umount and then **fsck /dev/sdd1** said it was clean.

I don't know my be bad to not backup the lost-found folder. I know the other hard drives has that same folder and it can copy them.

-Raymond Day

---

### Post by HermanAB on 2020-04-23
Cron loves quotes and full paths, since the cron environment variables are limited in scope.

Rsync works best when you include everything and exclude some things - to make the script maintenance free.

---

### Post by erind on 2020-04-23
> **Raymond Day said:**
> Thank you erind that worked for the last+found but why can't I copy it?

[...]

Can I just delete all that and start it over? Or I guess I get:

```
/media/4TB-Blue/lost+found/#169083091# ls
ls: cannot open directory '.': Permission denied
```

I am root on there too.

Is the lost+found folder for fix errors I guess.

Did a umount and then **fsck /dev/sdd1** said it was clean.

I don't know my be bad to not backup the lost-found folder. I know the other hard drives has that same folder and it can copy them.

-Raymond Day

Yes, you can delete lost+found directory, there's usually parts of previously corrupted files in there. The system will recreate that directory again.

[https://www.howtogeek.com/282374/what-is-the-lostfound-folder-on-linux-and-macos/](https://www.howtogeek.com/282374/what-is-the-lostfound-folder-on-linux-and-macos/) 

I think there's something wrong with the file/directory in your above code (169083091), but you need to check for every file/directory in lost+found. Keep in mind that "lost+found" directory is accessible only by root, so the rsync commands must be run as such, but it could be other things as well. 

You can always archive the lost+found directory (tar) before deleting it, then you can safely let rsync copy the whole disk with the tar archive of lost+found.

```
tar -czvf lost-found_archive_name.tar.gz /media/4TB-Blue/lost+found

sudo rm -rf /media/4TB-Blue/lost+found
```

 All that said, there's usually no harm in excluding the lost+found directory as shown in my previous post. Rather than dealing with lost+found at all, I'd do it this way:

```
rsync -avP --exclude 'lost+found' /media/....
```

---

### Post by SeijiSensei on 2020-04-24
I use the "--files-from" and "--exclude-from" switches with rsync.  Then I put the globs for the files I want to back up into one file, and the globs for ones I want to exclude into another.  For instance, one inclusion file looks like this 
```

etc/
home/
var/log
var/spool
usr/local

```
and the exclusion file like this
```

proc/
sys/
run/
dev/

```

---

### Post by Raymond Day on 2020-04-24
Thanks you for doing the commands right how I do it. That was good.

Did do the tar command and at the end it got errors like this:

```
/media/4TB-Blue/lost+found/#169083049/
tar: /media/4TB-Blue/lost+found/#169083091: Cannot open: Permission denied
/media/4TB-Blue/lost+found/#169083377/
/media/4TB-Blue/lost+found/#163446803
tar: /media/4TB-Blue/lost+found/#163446815: socket ignored
/media/4TB-Blue/lost+found/#163446858
tar: /media/4TB-Blue/lost+found/#163446903: socket ignored
/media/4TB-Blue/lost+found/#163446979
tar: /media/4TB-Blue/lost+found/#163446987: socket ignored
tar: /media/4TB-Blue/lost+found/#163447145: socket ignored
/media/4TB-Blue/lost+found/#163447161
/media/4TB-Blue/lost+found/#163447252
tar: /media/4TB-Blue/lost+found/#163447341: socket ignored
/media/4TB-Blue/lost+found/#163447411
/media/4TB-Blue/lost+found/#163447468
tar: /media/4TB-Blue/lost+found/#163447478: socket ignored
/media/4TB-Blue/lost+found/#163447481
/media/4TB-Blue/lost+found/#169082938
/media/4TB-Blue/lost+found/#169082940
/media/4TB-Blue/lost+found/#169082988
/media/4TB-Blue/lost+found/#169082996
/media/4TB-Blue/lost+found/#169083007
/media/4TB-Blue/lost+found/#169083041
tar: /media/4TB-Blue/lost+found/#169083043: socket ignored
tar: /media/4TB-Blue/lost+found/#169083048: socket ignored
/media/4TB-Blue/lost+found/#169083060
tar: /media/4TB-Blue/lost+found/#169083071: socket ignored
/media/4TB-Blue/lost+found/#169083072
/media/4TB-Blue/lost+found/#169083076
tar: /media/4TB-Blue/lost+found/#169083079: socket ignored
/media/4TB-Blue/lost+found/#169083082
/media/4TB-Blue/lost+found/#169083119
/media/4TB-Blue/lost+found/#169083206
/media/4TB-Blue/lost+found/#169083209
/media/4TB-Blue/lost+found/#169083222
/media/4TB-Blue/lost+found/#169083239
/media/4TB-Blue/lost+found/#169083247
/media/4TB-Blue/lost+found/#169083301
/media/4TB-Blue/lost+found/#169083309
tar: /media/4TB-Blue/lost+found/#169083314: socket ignored
/media/4TB-Blue/lost+found/#169083316
/media/4TB-Blue/lost+found/#169083346
/media/4TB-Blue/lost+found/#169083353
/media/4TB-Blue/lost+found/#169083370
tar: /media/4TB-Blue/lost+found/#169083387: socket ignored
/media/4TB-Blue/lost+found/#169083391
/media/4TB-Blue/lost+found/#169083415
/media/4TB-Blue/lost+found/#169083430
/media/4TB-Blue/lost+found/#169083433
tar: /media/4TB-Blue/lost+found/#172097540: socket ignored
/media/4TB-Blue/lost+found/#172097547
/media/4TB-Blue/lost+found/#172097555
/media/4TB-Blue/lost+found/#172097664
tar: /media/4TB-Blue/lost+found/#172097668: socket ignored
/media/4TB-Blue/lost+found/#172097675
/media/4TB-Blue/lost+found/#172097679
/media/4TB-Blue/lost+found/#172097683
tar: /media/4TB-Blue/lost+found/#172097732: socket ignored
/media/4TB-Blue/lost+found/#172097761
/media/4TB-Blue/lost+found/#172097765
/media/4TB-Blue/lost+found/#172097779
tar: /media/4TB-Blue/lost+found/#172097969: Cannot open: Device not a stream
/media/4TB-Blue/lost+found/#172097983
/media/4TB-Blue/lost+found/#172098034
/media/4TB-Blue/lost+found/#172098036
/media/4TB-Blue/lost+found/#172098039
/media/4TB-Blue/lost+found/#172098040
/media/4TB-Blue/lost+found/#172098041
tar: /media/4TB-Blue/lost+found: file changed as we read it
tar: Exiting with failure status due to previous errors
root@rayday:/media/4TB-Blue/lost+found#
********************** Sophos Anti-Virus Alert ***********************
Error scanning file
"/media/4TB-Blue/lost+found/#172097969".

Access to the file has been denied

**********************************************************************
```

Going to see if I can just delete it now.

But I get this:

```
rm -rf /media/4TB-Blue/lost+found
rm: cannot remove '/media/4TB-Blue/lost+found/#169083091': Operation not permitted
rm: cannot remove '/media/4TB-Blue/lost+found/#169083247': Operation not permitted
rm: cannot remove '/media/4TB-Blue/lost+found/#169083415': Operation not permitted
rm: cannot remove '/media/4TB-Blue/lost+found/#169083433': Operation not permitted
```

How can I delete them when root is "Operation not permitted"?

-Raymond Day

---

### Post by Raymond Day on 2020-04-24
It did delete that ones it could now I have a dir and 3 files in it. It looks like this:

```
:/media/4TB-Blue/lost+found# ls -l
total 100
dr-s-wsrwT 2 1480476685 2631567745  4096 Sep  5  2134 [COLOR="#00FF00"][COLOR="#00FF00"]'#169083091'[/COLOR][/COLOR]
--wS--Sr-- 1   79085352 3961470957 32768 Apr  5  2268 [COLOR="#FF0000"]'#169083247'[/COLOR]
---Sr-x--- 1 2496828555 1168384648 45056 Nov 14  2116 [COLOR="#FF0000"]'#169083415'[/COLOR]
--wSr-x--- 1   21444235  436242568 49152 Jul  1  2278 [COLOR="#FF0000"]'#169083433'[/COLOR]
```

Don't get why root can't delete them.

-Raymond Day

---

### Post by erind on 2020-04-24
> **Raymond Day said:**
> It did delete that ones it could now I have a dir and 3 files in it. It looks like this:

```
:/media/4TB-Blue/lost+found# ls -l
total 100
dr-s-wsrwT 2 1480476685 2631567745  4096 Sep  5  2134 [COLOR=#00FF00][COLOR=#00FF00]'#169083091'[/COLOR][/COLOR]
--wS--Sr-- 1   79085352 3961470957 32768 Apr  5  2268 [COLOR=#FF0000]'#169083247'[/COLOR]
---Sr-x--- 1 2496828555 1168384648 45056 Nov 14  2116 [COLOR=#FF0000]'#169083415'[/COLOR]
--wSr-x--- 1   21444235  436242568 49152 Jul  1  2278 [COLOR=#FF0000]'#169083433'[/COLOR]
```

Don't get why root can't delete them.

-Raymond Day

It's got to be something wrong with these leftover files/directory. [SIZE=2]What's the filesystem of this 4TB-Blue drive? NTFS, EXT4?* [ EDIT: It's got to be EXT4 ]*[/SIZE]
Can you run this command and post the output:

```
cd /media/4TB-Blue/

sudo find lost+found/ -ls
```

Worse comes to worst you can always re-format this drive and copy the files back over again into it.

---

### Post by Raymond Day on 2020-04-25
Here is that command I think it just shows what's in that lost+found folder.

```
sudo find lost+found/ -ls
       11     16 drwxr-xr-x   3 root     126         16384 Apr 24 08:04 lost+found/
169083091      4 dr-s-wsrwT   2 1480476685 2631567745     4096 Sep  5  2134 lost+found/#169083091
find: &#8216;lost+found/#169083091&#8217;: Permission denied
169083247     32 --wS--Sr--   1 79085352 3961470957    32768 Apr  5  2268 lost+found/#169083247
169083415     32 ---Sr-x---   1 2496828555 1168384648    45056 Nov 14  2116 lost+found/#169083415
169083433     32 --wSr-x---   1 21444235 436242568     49152 Jul  1  2278 lost+found/#169083433
```

```
(parted) print
Model: Unknown (unknown)
Disk /dev/sdd1: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags:

Number  Start  End     Size    File system  Flags
 1      0.00B  4001GB  4001GB  ext4

(parted)
```

Guess if any thing could format this again and **rsync** everything back, But the lost+found folder. Then would show it that root can do anything. :)

O you all ready said that I did not read to the end of your post before I typed that.


-Raymond Day

---

### Post by erind on 2020-04-25
I strongly think there's a filesystem error regarding these lost+found files, especially #169083091 directory. That is if, God forbid, it's not a hard disk hardware error. 

Before going the format route, can you run these commands in 4TB-Blue and show me the result:

```
cd /media/4TB-Blue/

sudo find lost+found/ -inum 169083091 -delete

sudo find lost+found/ -inum 169083247 -delete

sudo find lost+found/ -inum 169083415 -delete

sudo find lost+found/ -inum 169083433 -delete
```

---

### Post by Raymond Day on 2020-04-26
Thank you.

But looks like just get a "Operation Not Permitted" on all 4 of them.

```
root@server:~# cd /media/4TB-Blue/
root@server:/media/4TB-Blue# sudo find lost+found/ -inum 169083091 -delete
find: ‘lost+found/#169083091’: Permission denied
root@server:/media/4TB-Blue# sudo find lost+found/ -inum 169083247 -delete
find: ‘lost+found/#169083091’: Permission denied
find: cannot delete ‘lost+found/#169083247’: Operation not permitted
root@server:/media/4TB-Blue# sudo find lost+found/ -inum 169083415 -delete
find: ‘lost+found/#169083091’: Permission denied
find: cannot delete ‘lost+found/#169083415’: Operation not permitted
root@server:/media/4TB-Blue# sudo find lost+found/ -inum 169083433 -delete
find: ‘lost+found/#169083091’: Permission denied
find: cannot delete ‘lost+found/#169083433’: Operation not permitted
root@server:/media/4TB-Blue#
```

-Raymond Day

---

### Post by erind on 2020-04-26
In this case backup the drive excluding lost+found directory, format the whole drive and rsync back all the files again. After that run a check disk again and rsync the whole drive and look for errors to make sure it works properly. 
Again I hope it's not a hardware problem.

---

### Post by Raymond Day on 2020-04-27
Here is the SMART data.

```
LU WWN Device Id	5
Firmware Version	80
User Capacity	4,000,787,030,016
Sector Sizes	512
Rotation Rate	5400
Form Factor	3
SATA Version is: SATA 3.1, 6.0 Gb/s (current	6
SMART Attributes Data Structure revision number	16
Raw Read Error Rate	0 (Normalized: 200)
Spin Up Time	6616 (Normalized: 167)
Start Stop Count	1261 (Normalized: 099)
Reallocated Sector Ct	0 (Normalized: 200)
Seek Error Rate	0 (Normalized: 100)
Power On Hours	17005 (Normalized: 077)
Spin Retry Count	0 (Normalized: 100)
Calibration Retry Count	0 (Normalized: 100)
Power Cycle Count	72 (Normalized: 100)
Power-Off Retract Count	47 (Normalized: 200)
Load Cycle Count	15646 (Normalized: 195)
Temperature Celsius	39 (Normalized: 111)
Reallocated Event Count	0 (Normalized: 200)
Current Pending Sector	0 (Normalized: 200)
Offline Uncorrectable	0 (Normalized: 200)
Multi Zone Error Rate	0 (Normalized: 200)
SMART Error Log Version	1
```

At the end here is does say 1 error.

Going to format it.

-Raymond Day

---

### Post by Raymond Day on 2020-04-27
Wow what is the right way to format it? What command do I use?

I was trying unmounting it and thought I formatted it but it comes back fast and mount it again and all still there.

-Raymond Day

---

### Post by Raymond Day on 2020-04-27
Here is what I get.

```
parted /dev/sdd
GNU Parted 3.2
Using /dev/sdd
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) mklabel gpt
Warning: The existing disk label on /dev/sdd will be destroyed and all data on this disk will be lost. Do you want to continue?
Yes/No? yes
(parted) unit TB
(parted) mkpart primary 0 0
(parted) print
Model: ASMT ASM1156-PM (scsi)
Disk /dev/sdd: 4.00TB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name     Flags
 1      0.00TB  0.00TB  0.00TB               primary

(parted) mklabel
New disk label type? 4TB-Blue
parted: invalid token: 4TB-Blue
New disk label type? linux
parted: invalid token: linux
New disk label type? ?
parted: invalid token: ?
New disk label type? 4tb
parted: invalid token: 4tb
New disk label type? msdos
Warning: The existing disk label on /dev/sdd will be destroyed and all data on this disk will be lost. Do you want to continue?
Yes/No? yes
(parted) print
Model: ASMT ASM1156-PM (scsi)
Disk /dev/sdd: 4.00TB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags:

Number  Start  End  Size  Type  File system  Flags

(parted) mkpart
Partition type?  primary/extended? primary
File system type?  [ext2]? ext4
Start? yes
Error: Invalid number.
(parted) mkpart
Partition type?  primary/extended? primary
File system type?  [ext2]? ext4
Start? 0%
End? -1s
Error: partition length of 7814037167 sectors exceeds the msdos-partition-table-imposed maximum of 4294967295
(parted
```

Just before it goes to format I guess it does Error.

-Raymond Day

---

### Post by Raymond Day on 2020-04-27
Got it formatted.

Now copying back the data did this command.

```
rsync -avP /media/12TB-backup/4TB-Blue/ /media/4TB-Blue
```

Going to take some time to copy all that back.

Mostly did:

```
umount /dev/sdd1
mkfs.ext4 /dev/sdd1
```

That made it work. After I did parted commands on it.

-Raymond Day

---

### Post by erind on 2020-04-27
> **Raymond Day said:**
> Wow what is the right way to format it? What command do I use?

I was trying unmounting it and thought I formatted it but it comes back fast and mount it again and all still there.

-Raymond Day

I'm not sure if there's an error in your last line of the log. But let's try Gparted to format the drive, it's in the repositories, and see how it goes. If Gparted fails as well then we're dealing with a hardware error, but let's go one step at a time.

--

EDIT: Just saw your last post. Good job! Let us know how it goes!

---

### Post by Raymond Day on 2020-04-27
I was doing the rsync copy and seen my file system was 100% used the / main part.

Trying to see what was wrong and looks like I did not mount the drive when I did the rsync. So I guess it was trying to do it at the main file system. I got a 1TB drive for it.

When I found it was not mounted I stop the rsync with CTRL-C and rebooted.

It still shows no room left on /

```
/dev/sdb2       916G  911G     0 100% /
```

So 100% used. How can I tell what files are using all the space. I guess it was trying to rsync it there some place.

The 4TB is mounted now.

-Raymond Day

---

### Post by Raymond Day on 2020-04-27
Wow just don't know what file is filling it up. I got WordPress on this server and I can't update it. It just shows "Updating..." and never gets done.

How can I found out what is using all the room on it?

don't know why rsync did not give a error when it was copying to a none mounted drive.

-Raymond Day

---

### Post by Raymond Day on 2020-04-27
It's the boot and I can't find the what is making it use 100%

I my have to redo it and that will be hard to get it how I have it now.

It show this.

/dev/sdb2       916G  911G     0 100% /

It the boot on a SATA SSD 1TB 3D NAND.

Because it's full a lot of things not work now. Very hard to find what is full it now.

-Raymond Day

---

### Post by erind on 2020-04-27
> **Raymond Day said:**
> Wow just don't know what file is filling it up. I got WordPress on this server and I can't update it. It just shows "Updating..." and never gets done.

How can I found out what is using all the room on it?

don't know why rsync did not give a error when it was copying to a none mounted drive.

-Raymond Day

Try this command and post its output:

```
sudo du -sh  /* | sort -h -k1
```

It'll show the directories with their disk usage sorted, with the biggest dir on the bottom. Then we can look further into it.

---

### Post by Raymond Day on 2020-04-28
Wow took a long time to find it.

I got folder's that are mounted in /media and the name "4TB-Blue" is a folder but It's mounted to it. So it put it on the main boot. So I deleted it and made a new folder same name.

Now my boot drive is "/dev/sdb2       916G  126G  744G  15% /"

So only 15% filled a 1TB SSD.

To have a drive mounted have to have a folder right? That's bad because the folder is still there if the drive is not mounted. Is there some other way to mount them so that if it is not mounted it don't show as a folder?

Thank you.

-Raymond Day

---

### Post by erind on 2020-04-28
> **Raymond Day said:**
> Wow took a long time to find it.

[...]

To have a drive mounted have to have a folder right? That's bad because the folder is still there if the drive is not mounted. Is there some other way to mount them so that if it is not mounted it don't show as a folder?

Thank you.

-Raymond Day

Great that you found the place! Now you're not supposed to manually create directories in /media, that's because the system will create automatically the mount points (directories) for the external drives in /media. So delete any directories that you created in there (/media). Leave it empty!

Now, if your system for some reason is not able to auto-mount the external drives, then you got another problem that you need to fix. In any case to make sure that rsync command runs only when the drive is mounted then you check first if it's mounted, something like (**mount | grep '/dev/sdb2/'**) or you can create a flag file in the root directory of 4TB-Blue drive, say a file named **flag_file_for_rsync_Apr-28-2020** and then check for that flag file before starting rsync (** [ -f flag_file_for_rsync_Apr-28-2020 ] && rsync -avP .....** ) and so on.

But I think the best way is to let the drive mount automatically and check for its mounting before starting rsync. Let us know how it goes.

---

