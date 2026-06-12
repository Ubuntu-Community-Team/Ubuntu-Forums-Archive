---
title: "Ubuntu multiple network folder share with permission to Windows 7"
date: 2013-12-04
forum: General Help
---

### Post by snooze101 on 2013-12-04
Hi,

I am trying to setup a network share between a Ubuntu 12.04 system (file server) 64bit ext4 and Windows 7 Pro 64bit machines.

The folder and access levels for the folders on Ubuntu 12.04 file server should be setup as below.

**/home/User01/Downloads**
**Read Access**
User01
**Write Access**
User01

**/media/HDD01/Audio**
**Read Access**
User01
**Write Access**
User01

**/media/HDD01/RsyncBackup**
**Read Access**
User01
User02
**WriteAccess**
User01
User02

[B]/media/HDD02/Movies
Read Access[/B]
User01
User02
**Write Access**
User01

_Could you provide me what should be the **chmod**, **chown**, **what value the folder should ie 777**, **etc** for this to work successful while maintaining a reasonable level of security._

**No other users on the local network should be able to access the folders on the network with the User01 or User02 password.**

I am new to file permissions configuration on linux in general. 

I have some experience in setting up SAMBA users, SAMBA users without login access, configure the smb.conf file, configure the fstab file. I haven't been able to find a tutorial that about permission which is where I think my setup is not working. I would apprepiate an explanation on the steps on how to setup this, that way I know what each setup is actually doing to the file permissions etc.

_Do I need to increase my knownlodge in groups file permission in Linux to get this setup working._

Also not sure if this post in the correct location, not sure if this is networking issue.

regards
Snooze101

---

### Post by Morbius1 on 2013-12-04
The first one is easy since it will do that without any chown'ong or chmod'ing:
```
[Downloads]
path = /home/User01/Downloads
valid users = User01
read only = No
```
The next series can be complicated depending on how it's formatted ( NTFS ? ) and how it's being mounted. What is the output of the following command:
```
ls -al /media/HDD01
```

---

### Post by snooze101 on 2013-12-04
Thanks Morbius1, I have included the ls results below.

I have  updated the original post to indicate that the Audio and RsyncBackup are  located on the 1st hard drive (formatted with Ext4) and Movies located  on the 2nd hard drive (formatted with Ext4).

[B]/media/HDD01/Audio
**/media/HDD01/RsyncBackup**
[/B]
**/media/HDD02/Movies**

The output of the ls command for HDD01 is as below.
total 216
drwxr-xr-x  20 User01 User01  4096 Nov 10 15:44 .
drwxr-xr-x   9 root  root   4096 Dec  3 22:27 ..
drwxrwxr-x   2 User01 User01  4096 Jul 20 12:49 AudioAudioBooks
drwxrwxr-x   6 User01 User01  4096 Oct 20 22:45 AudioMusic
drwx------  43 User01 User01  4096 Sep 11  2012 AudioUnsorted
drwxr-xr-- 688 User01 User01 32768 Aug 20 11:38 AudioUnsortedMusic
drwxrwxr-x   6 User01 User01  4096 Oct  1  2012 AudioUnsortedMusicIncomplete
drwx------  18 User01 User01  4096 Aug  3  2012 AudioUnsortedPodcasts
-rw-rw-r--   1 User01 User01 82726 May 26  2013 AutorunDriveIcon256.ico
-rwxrwxrwx   1 User01 User01    40 Jun 10  2010 Autorun.inf
drwxrwxr-x  10 User01 User01  4096 Nov 15 18:38 Backup
drwxr-xr-x   5 User01 User01  4096 Aug 20  2012 Career
drwxr-xr-x   8 User01 User01  4096 Jul 21  2012 CDandDVDImages
drwxrwxr-x   4 User01 User01  4096 Nov 10 13:55 DeleteReady
drwx------   4 User01 User01  4096 Mar 15  2010 Guitar
drwx------   2 User01 User01 16384 May 26  2013 lost+found
drwx------   7 User01 User01  4096 Oct 30 19:54 Software
drwx------   5 User01 User01  4096 May 26  2013 .Trash-1000
drwx------  36 User01 User01 12288 Jun 11  2010 UnsortedVideo
drwx---r--  24 User01 User01  4096 Feb  2  2013 VideoComdey
drwx------  66 User01 User01  4096 Aug 18 12:59 VideoDocumentary
drwx------  32 User01 User01  4096 Feb  3  2011 VideoMusic

The output of the ls command for HDD02 is as below.
total 168
drwxr-xr-x   8 User01 User01  4096 May 26  2013 .
drwxr-xr-x   9 root  root   4096 Dec  3 22:27 ..
-rw-rw-r--   1 User01 User01 82726 May 26  2013 AutorunDriveIcon256.ico
-rwxrwxrwx   1 User01 User01    40 Jun 10  2010 Autorun.inf
drwx------   2 User01 User01 16384 Jun 26  2012 lost+found
drwx------   5 User01 User01  4096 Jun 26  2012 .Trash-1000
drwxrwxr-x 635 User01 User01 36864 Nov 19 06:31 VideoMovies
drwxrwxr-x   5 User01 User01  4096 Aug 14  2012 VideoMoviesCAM
drwxrwxr-x 102 User01 User01  4096 Jul 19  2012 VideoMoviesISO
drwxrwxr-x  14 User01 User01  4096 Jul 19  2012 VideoMoviesISONotCopied

regards
Snooze101

---

### Post by Morbius1 on 2013-12-04
If these are all ext4 then this gets simpler.

[] /media/HDD01/Audio will look exactly like the example I gave for your Downloads folder:
```
[Audio]
path = /media/HDD01/Audio
read only = No
valid users = User01
```
[COLOR=#0000cd]*You already own the folder with write access so there's nothing else to do here.*[/COLOR]

[] /media/HDD02/Movies will be set to be read only but with the "write list" option:
```
[Movies]
path = /media/HDD02/Movies
valid users = User01, User02
read only = Yes
write list = User01

```
[COLOR=#0000cd]* By default this is a read only share but "write list" overrides this default for that one user so User01 can write and User02 can only read. The permission on all the HDD02 directories seem to be 775 with User01 as owner so you don't have to change anything of this either.*[/COLOR]

[] This is the hard one because I don't know how you intend to use it:
> **/media/HDD01/RsyncBackup**
**Read Access**
User01
User02
**WriteAccess**
User01
User02
Um ..... Let's try this for starters:
```
[RsyncBackup]
path = /media/HDD01/RyncBackup
read only = No
valid users = User01, User02

```
Then you need to change permissions on the target folder:
```
sudo chmod 0770 /media/HDD01/RsyncBackup
```
Change ownership to include a common group like plugdev:
```
sudo chown :plugdev /media/HDD01/RsyncBackup
```
And make sure both users are memebrs of the plugdev group:
```
sudo gpasswd -a User02 plugdev
```

Note: With that configuration both User01 and User02 will be able to read and write to the share but one user will not be able to edit any of the others files which I would suspect is something you want for a Backup.

I'm shutting down for the day so if you have any other question I will check in tomorrow - of course there is always the 2nd shift crowed here.

---

### Post by snooze101 on 2013-12-05
Thanks Morbius1 for your quick instructions and explanation, I'll try these settings and post an update if setup works.

regards
Snooze101

---

### Post by snooze101 on 2013-12-14
Hi Morbius1,

Thanks for your assistance on this ubuntu question. Your instructions work for the setup of share folder between ubuntu to window 7 network folder.

The only tweak required, was for the Rsync folder, probably did not explain it well. Rsync backupfolder will be used by user02 to backup files to, but when user01 should be able to have full access (ownership) to it. The code used is as below.

Changing permission of the folder, change ownership to include a common group, make sure both users are memebrs, as you describe in previous post was followed and worked.

```

[RsyncBackup]
    path = /media/HDD01/Backup/Rsync/User02
    valid users = User01, User02
    read only = No
    force user = User01

```

I am having **issue with permission for some of the shared folder**, if you or someone on the forum can provided assistance that would be appreciated.

When user02 on Win7 is trying to read a shared folder, an **error comes up as below**.
user01 can read (and not test but should be able to write) this folder fine.

[IMG]http://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAgsAAAC0CAYAAAAaXG9HAAAABHNCSVQICAgIfAhkiAAAHIdJREFUeF7tncuzZEtVh6uNDicqF3kEoigQhAre9t5WlL4q6u2Zf4ATJw6dKCqiEj5QW8XHxbf4DzjuQQ972CE um8IdEu3goaKIgEI ELH7cmqnVWr1lkrd2buvbMqq74K p69M9fjt77MvWuxT51zrjx eP/pihcEIAABCEAAAhBwCFwN488 f8OZZhgCEIAABCAAgXMmcOvWrdW6WQivJ48enDMLaocABCAAAQhAwCGwbRbC/Dt 8E/3zK5cubI93xxuznfDV1b28YXbxcTW  Jge7Y Dq/NweXjje9gMRgP3mtjeTycDYk208PJNsyQYfBdR9iaSP1hfOdbpn8TdBd2yCmKEOk3FQzG62q2xztxO/sh1i54ln65XpsUuyRDxLgEQeUaikgRKRv8feYbzdvoW98h/CZPiLxNtM/c2287RBeOm/8Fwdn6Zb1rLbsgm5oHQRv9Wwuz9rW3q3/ju6t3yLy1T2n2 V/WH4rYjqpjrX /3o22XQEec/sa2a89tWek5svHWr/WPLAYZHrrZXMesm1L9NerTP9G8y6s5K/16z12Ybutxa59V8sQK0M/1/gO6nY1tkPjzNemw392x5p/uLy2izFcdkM24SSvF3F7WV bW  942GPDBqGiIl9srUwNe9dI/IGFeJPfD335R9fR/iyiXFwhwAEIAABCEDgxAnsPVk48VopDwIQgAAEIHAWBH7oO5 prvPmzZurH3npzp4/zUI1ThwhAAEIQAACx0ug5rOIt /cNQvq8tsQn/3IS6vPfvglsyAGIQABCEAAAhCYl4D5ZOH//uFP1lm 8pt bJvtS5/44Oqrvvldyez/9bd/uJ5/5bf8RNKu1eSnX/6tS6necOPnL40xAAEIQAACEDhlAteuv7Au7 J3K 2V6Y1rFsknC//79x/U9l2ef907fm71hhvhH41ClwuIaAhAAAIQmEQgNgmxOQjBchuFYGs WZCKQsMgnzCEuf/5 B/viX7mbT  dx6fMHz1sz 5 s8nf7Cee9W1d6/ 4/Hvr49f/a3vXn3xY7 3Pn7Ncz 1/vqFR7 7/hpfr73 0 vDf//o76y/vu7bfmb1uY98YPW6b//ZrU08 Mxf//b68Gu/472X5qyBT93/jfXw17/wC6t//av3r77huzZfw9gbv/sXV//yl7  euP3vG9t88m/ LX11/h68/f 0vrwnz50a/31Ld/3y6t//LNbq7d8/69EE75CAAIQgAAEjo5AaBhCgyAbBv2kwRPtPln4im/80a2PfMLwpU9sGoVXvPVdq1e8ddMk/Pff/dFe/PBtiFdeNAq5ry/8zaZReO3z71mFf H1 YebJiHG NxHP2CG 8yHN43C6xONwqdf/s3Vvz0I/zZNQgz0qfvvvxQzNArxFRuFN73zfas3v3PTJPzzh351zyc0CrwgAAEIQAACPRCQzUFuoxDqSj5ZCE8UvG9F6KcLS0MKTxbiL9CIueKHHFONQrAN34bY wUmQ4DwZEH//orwZGH90hMxqfoaniyU2DthGIYABCAAAQgsTkB/GyK3YUg2C0G11zCEJwvr30G1 /VUySLjtyCC0Rc/tvl2RNKBSQhAAAIQgAAEZiOgP6MQvyWR0zC434aQ6vRnFkqUh88txFf43MKrLj6vEF vHj6vUBJP2n7N2zefX4ifWaiNgx8EIAABCEDglAnoRiHUan3o0WMw mRBO4YfnwyfW9DfhnjmbRefU7j4rEL4cKP8gKP2t85f89x7VuFzC58XH3IMH3DcPrSwnIax17/9vavwuYXQMHgfcAyfWYivkp IeNPFhxzD5xY  ee7DzmGDzjm6EpIZgoCEIAABCDQlID39MAb1 KuXBg DX iOvymJ/6QlGgDMv/ox 67MPt/MCSAXs8N/9kdD39AZHD0/kiO9F2H2SVyjoPNTv/eZzQuhrfq1seDsO3xJoFIsWe/9R4M0pq30SWATM0p/VrzRvxOs Tv17uJsit87T9w2xxvLbb6d PD3E6my1zy3/tW3S71Om dfq15E8XWP7BwNe8mPM323kvvma2ibb2bA1nvsKIG54HLYOztt93SDdnWX Rxer32 ft7RmrO07/P3NO/k5vSfOG9TRq2zO5Erlcom2t8DWH9ymEu e O03vm8jVyee02a7HRcYhrPO6R8Ouea3 D471797a/7jn8IanwWx2LnywMCPgCAQhAAAIQgMARE/B dXONZJqFGmr4QAACEIAABI6YQPhjUHO aBbmpEksCEAAAhCAwBEQ0H81cqqkrJ GmJoEfwhAAAIQgAAE iWw92Th5ds/3G8lKIcABCBwEgSeiirk8UkURxGdEuDJQqcLh2wIQAACEIBAKwI0C61IkwcCEIAABCDQKQGahU4XDtkQgAAEIACBVgRoFlqRJg8EIAABCECgUwI0C50uHLIhAAEIQAACrQjQLLQiTR4IQAACEIBApwRoFjpdOGRDAAIQgAAEWhGgWWhFmjwQgAAEIACBTgnQLHS6cMiGAAQgAAEItCJAs9CKNHkgAAEIQAACnRKgWeh04ZANAQhAAAIQaEWAZqEVafJAAAIQgAAEOiVAs9DpwiEbAhCAAAQg0IoAzUIr0uSBAAQgAAEIdEqAZqHThUM2BCAAAQhAoBUBmoVWpMkDAQhAAAIQ6JQAzUKnC4dsCEAAAhCAQCsCNAutSJMHAhCAAAQg0CkBmoVOFw7ZEIAABCAAgVYEaBZakSYPBCAAAQhAoFMCNAudLhyyIQABCEAAAq0IHG2zcO36C6vwj1d/BLx188aXqHDuXOzHzSrNzXWJtZcxU t2SrUszZH4ELhagyBeZI8f3l 7p871XE2 c/I5V17WjVvvr7gP4ng8L2GmbeW5npt731k1hhyhHp3bO5eaNIccvTpujk uja5P6kvN6XWcWmOu3pRdSm9q7lhq0RqDrpr9kmI0dU5r1PqW3KtTtZ j/ JPFsIG0JvgHEGfU83yzU/W7Y3Lm0LcL3HP6LkQT95k9A0n5vNypdZh6b2q4 tzT5tmkOtnxZviG J5XLVGuU6puTGN3vpafqVjp1SLrF3znrrmpVxz7LVGuV/0cU48bJYnUPVkoUSW3BTWhR82cnxZ895c9LPiy5uAtovxZN7cHNrX0uvlC76pWrUeWdcW0HCg8 bE9Xy88ZDKm/PGtc4W53Ktp bTzHWdMr6ey1mDqfo8f0 LrCccS1bePq2tQ 9fT vUca/WEDc1F/PqNbb0nFItVn0pTjVzno8eD1py2c55XVsMGCsnUNUsxIWMNyCZtuRiDLYxhvaTG82as3J75Wt/yy5lo2 gOre88ebM6Vzh3POztHp6dNzomzsudeT6WPrCWNwj ubgjXtxpoxbueTejbG1xjCu64/n3lxcP8svzqVqydElNUTNOfmkn9SQ8tVz0s/iGuctjam6S a0pnAe/kU9IZa1llqbtDmlWjRLay1SDDW/HL5j8WRMGU9r5fz4CVQ1C7IsuSHl8TGWrjd2rsZjq2tuPal4HjNvPJfpKdiluM1Zn3wzjHFDbvmml9KSegMN8VK pesccwU/rTGXidQzpr00Zkm8XmuZsl9Se0HulRKOuWuE3XETmNwshPLkRXWocuUm1xteXzwlNzF9s9SxW9e7hB7rwveYeeOtORxDPovbUrpkLmsPTtFi R5ynXXupZi2iHuoWmr2S reousouYe24EyO5QlUf8DRusFEuam5uUuSucKxPpeaWuqau85DxNM8S1nqG4z0t97wlqjR0uDtkSXyl8Q8Nl3e oeaNNewnnOuaWQxV8xUvFOqpWS/ldqm9kNpLOz7I3DlYgM8ffb5G6snjx4Uq/c6UXnTkzZj9taNwbvIvRyhCC9PLFD6yqJ1fi938JE3GG03Nic1WpqkDkur1hn1pOJqH61ZcpD6tT4vjvSXx8Heq0GO67g5NaXqHdOg94iMNcbGypur18qjtcpYY7lS81Nq1OtRs4ap9fXiebV7azKWQzPQ55G93qep lNzMt4ha5F7ytMhbTy 0TdVszenWXvnUcfYWuqaOG9H4Padu6tJzUI7qWTqmYC EcdavPElam2Zawn9xxrzlLieUi3Hul/Q1SeB0CxUfxuiz5JRDQEIQAACEIBAKQGeLJQSwx4CEIAABCBwRgR4snBGi02pEIAABCAAgVoCfBuilhx EIAABCAAgTMhQLNwJgtNmRCAAAQgAIFaAjQLteTwgwAEIAABCJwJAZqFM1loyoQABCAAAQjUEqBZqCWHHwQgAAEIQOBMCNAsnMlCUyYEIAABCECglgDNQi05/CAAAQhAAAJnQoBm4UwWmjIhAAEIQAACtQRoFmrJ4QcBCEAAAhA4EwI0C2ey0JQJAQhAAAIQqCVAs1BLDj8IQAACEIDAmRCgWTiThaZMCEAAAhCAQC0BmoVacvhBAAIQgAAEzoQAzcKZLDRlQgACEIAABGoJ0CzUksMPAhCAAAQgcCYEjrZZuHb9hYMswaHyHqRYkl4ioNdfn19ymDAwNfZU/wnSF3c9xtosTdbY4nBGEhyjphHJTHdA4GqNxrAZHz 8v3XV5zUxW/r0preWTWmdpfaWrjliWHGPbUzfkOP1IMflNRL0j7HR8/Fcj09lobWHeEGrziPPtY uLaVJx03ZpuakBn3/iX6WrinaU3q8uR50tmbisQrjHq84Z61pbrxgV pfmzdqmmu/p2o8xFxVs3AIoeQsJ1B6kZTalys6DQ/vZqDH5bm OZeQmHtdYjyt19OUa f5z6Ffa4jn3rjWIjVoH2075VzHPkadWuOUeqf6ai3yPByXvnS8Un/sfQJVzUK48FIXQUzn3ZS8BfU2hxy3bjzaT98YtJ5wHn3G4o3F0rXI87l1x9jyq6xN1zSmResrsQ95LXYWW50napZfPRtrPHdMapF6LX/NMdYm93qM59Vt1aXjShsd2/P31kXaezV5416u0nErftSrv0Z kkk81nE0mxrmubXo3J4mzTto6kXnUiwsdmNjQUvOeka2JdpTcUt1RfsY0/IP2qxx7Sv3lNQY7FLx5XzMJfecns9lVWNX1Sx4ibRwfe75SQgSqjdubQhrAXR eW7FiLmtWGHOG7fqSuWW9lbMlK ekxvNOrYYemNRl87hcdN2Y/xSeXM4eP5aRzzX456/XI9DHgcGJdqDrVWTF8PiIev18sfxaJuzz6xceszTmVqDWLPcLyn7sbkaTdrHynHMOmvWs/b6lKysGBa7Jcb0muXo0nvM0q/j6msktxYdR59bcXJsLL/asepmIW44DbRWSA9 8QYgtUoOevEs 9w6Pd9a3lpb0GGN5eqb286rNzeP52/VaI3l5jlWO6/ ufRaN8q4h6wc3j71dOauSYybax 1ybyeNqsOPZab99h1lq7n1HXTHHs89xiU1JJ6vyiJE2yn7OPSXMG ulmoSdazj75J5GycKYs5xVdzljeuuMmsMe3X6ryGrdZm8bJqtMZ0rB7Prfpb1FGa17JvsSY6Ry2bEEfv19pYlt hdVrro uN9z6t1fK1auxxzGPQYy21mo/2RydrCzqEX84NJKe58LRP8ZUxrYvZGvN09DKueVk1WmM59cW1zrGtscnZS2Nxdf1j9nqP6Btjrn9pXm2fWhNtm6tJ282xfqkYvejUXKzz3FpS62bFnTrm6Uqty9Scc/rPcY3PqSc31qxPFvRixU2kxy1xno0eL9mYnq8cz42nY1k1yDFt7 WRGz/a5PqOaYjzVg5rLNpPya/Z5sTSNikd2jacW2MhhlWjNaY5xnjha3h559IvpUNqCfljXCu21qJzWDdKr35vPJXDmtM5NZfoI uy4nh6vDWR3D1fb9zKL3XGdfD8vfFUjODj XnjLXXGXKXrqbVbcYJNeGnbOO7VmbKPOvU148Wy8sexVB4rnrQPx9o/ uhxbTtWfyqOV4 lt8XYlYtinj77/I3Vk0cPWuQjhyBQchEAri0BvTb6fE41S8aeU chYvXCphedh1hDcu4T6HGv3L5zd8W3IdjJEIAABCAAAQgkCfBkIYmHSQhAAAIQgMB5E DJwnmvP9VDAAIQgAAEsgh0/W2I8L2fOV5zxZlDCzEgAAEIQAACx0agSbNwKm/GY3Wk5lNzqU1R6ydjzhEjpXGpuV51L8WDuBCAAAQORaBJs3Co4ubOO/ZjMGPzc shHgQgAAEIQKAFgarfs6D/H598k5Rz1nj8udQ4F y94whAz0ufaGONhbkxPRKyto3nVn7pp e9vDJe1Kvr1zXLWDKPtrPiWbWlYmh7a610Xl1rONd 0WYst YvY0dfrXFMTyqnlU/Xk/KXWjiGAAQgcMoEqpqFAETevL03KvlGaN3sPbDSL9joN1QdS9vLuLk6o498c7COtZ3WZ51bPpadpTXYeeM6RimHqMvzS3FPrXmMa33Vubw4HjMZ0 Ki42tGXs0pHVZMqzbGIAABCJwqgepmwQMSbqy5r9QN2otR0iiEGCV6vJw14zlvMFYtNbmij443JVbw1fHmYunFyWEma/Li5Nbt Vs6rLHcPNhBAAIQ6J3A7M2CfoNZGlDI593I9bj35jC3xsgg5sthciitJbXn1JETz4pTymwOXrk6SrXlMMAGAhCAQE8EFv2Ao/fmrN/g9XkpwOhf6re0vfVmtHTOVvG9tS3Nr McilmODq1N 5TWjj0EIACBXgjM mRBv2nHm6sc1zdcC5QXx7KNY9FHxtdxtG0q3pQ5 SaSyyBHa7DRdrJeT7P0mSNGyGPVJfNrnR77GKeUWUl8bZtiYOmwxjzWjEMAAhA4RQL8uudTXNUD1hTeWGMDcEAZpIYABCAAgZkI8OueZwJJGAhAAAIQgMApE1j0MwunDI7abAI8VbC5MAoBCECgZwI0Cz2vHtohAAEIQAACDQjQLDSATAoIQAACEIBAzwRoFnpePbRDAAIQgAAEGhCgWWgAmRQQgAAEIACBngnQLPS8emiHAAQgAAEINCBAs9AAMikgAAEIQAACPROgWeh59dAOAQhAAAIQaECAZqEBZFJAAAIQgAAEeiZAs9Dz6qEdAhCAAAQg0IAAzUIDyKSAAAQgAAEI9EyAZqHn1UM7BCAAAQhAoAEBmoUGkEkBAQhAAAIQ6JkAzULPq4d2CEAAAhCAQAMCNAsNIJMCAhCAAAQg0DMBmgW1eteu312Ff6f2OsWaTm2Nlq7nGPdAS00tcy29lsSHQGsCVc1CfEOVX1sLr8k3drMI848f/sD6X4uX1qPPW2gozXFIjaW5S 1LWSxlr3V753p8KT25cS091lhuvFZ2QaP81yqvzNMDp0NwIefxELhaK6XVG2qtPsvv2DUfuz6LacuxUj6l9i1rmSPXqdc3B6OxGOFNGo5jlJiHwGpV3Sx48GSHHC/CeEFaF6a2j fyAtY2IbcV07KTOqWPHLdySe3R1qtH582tIdYRvobYUZ8cj3N6TI5HffGr1lMzLrXE3JqJvsnKvFqfpUmuR6w/apXnmrtmoXXF3FN4Wno1Z3lu2VtjnvZUbG9O8pM2cl30mkQ7S5vmlcvd06fHrZyWnjCm95ZlZ6279vXq19r0uWQR5sZY6zzeGmimmrnWr3VxDoFDEahuFqyLw7vA5MVmFaovIGmfGzNll8qptemL3DvX VI1hBxeHDkederY8tyLI2v0bKzxVC6Lm65F25Tm0PnHOOr18phJXTrHGE9tr2vU55a9Hovn3riMGRhoe32uNeRyt/hpTTp2DmNpY/nrHPo8 Fg16FiejTWuc4Rz/Yqs47iMo20tG5kjV0O00/pycnuaGIfA0gSqm4XSjV1qn1O4jmndDHLi1Njo3GMxWmprmWus7jjvaSrlKONpX33zzdVm2ZXGsuy9mr1xS8chxmItXk2au9So52Stc9Q9RwzNVGq2atb2c51rVnPFJQ4EliBQ3SwsIWZqzGO9 PQNaIkbXmTXMlfJes25NjFW5BjOrbESfdK2NJZn79XsjdfqbeXn1Zmbf2rdx7q3c vHDgI9E6j6aYgeCl7yDbmH o9Z41xrY735WGO1LHSsMd3aXub1fL3xEEu Oerz2ppSfjqHPo  qTpT8XN45PpjBwEItCUw65OFeHOZ86aSGzPXrgTvXDF1HMlH/r9jazyMldycvVwhjnxjijG1vTduabN0leQoWQtpa WwxizNOTxTsSzNln0uV4uhlaNmTGuo5RH9rDpzdWktVt1j8XWMsdw59jKn3BspX0 nNa7jWHXHvNHfsxmrl3kILEngyuOH958  /yN1ZNHD5bMQ wzIBBudqd8ozv1 g65RXth6 n0xg/JlNwQmIvA7Tt3V1XNguyg5xJDHAhAAAIQ2BA45aabNe6PQGgWqr4NwUbub7FRDAEIQAACEKglcLIfcKwFgh8EIAABCEAAAvsEaBbYERCAAAQgAAEIJAnQLCTxMAkBCEAAAhCAAM0CewACEIAABCAAgSQBmoUkHiYhAAEIQAACEKBZYA9AAAIQgAAEIJAkQLOQxMMkBCAAAQhAAAI0C wBCEAAAhCAAASSBGgWkniYhAAEIAABCECAZoE9AAEIQAACEIBAkgDNQhIPkxCAAAQgAAEI0CywByAAAQhAAAIQSBKgWUjiYRICEIAABCAAAZoF9gAEIAABCEAAAkkCNAtJPExCAAIQgAAEIECzwB6AAAQgAAEIQCBJgGYhiYdJCEAAAhCAAARoFtgDEIAABCAAAQgkCdAsJPEwCQEIQAACEIAAzQJ7AAIQgAAEIACBJAGahSQeJiEAAQhAAAIQoFlgD0AAAhCAAAQgkCRAs5DEwyQEIAABCEAAAldBAAEIQAACEDhXAteuv3CWpT9 eL obp4sFOHCGAIQgAAETo3A06dPV fy78UXX6xaPp4sVGHDCQIQgAAETonAk0cPTqkcs5bbd 6a4zmDPFnIoYQNBCAAAQhA4IwJ0Cyc8eJTOgQgAAEIQCCHAM1CDiVsIAABCEAAAmdMgGbhjBef0iEAAQhAAAI5BGgWcihhAwEIQAACEKgkcAo/nslPQ1QuPm4QgAAEIAABTUA3BqW/z0DHO5ZzmoVjWQl0QAACEIBA1wRCo3AqzYFeCJoFTYRzCEAAAhCAQCGB3EZBPnmQjYU1bo0VyprNnGZhNpQEggAEIAABCPgEdEMRz/V4iKDH9LmfZZkZmoVluBIVAhCAAAQgkE3Aagbkk4XsQAsZ0iwsBJawEIAABCAAgRwC8dsRsTmI58f0 Qd dDJnJbGBAAQgAAEIJAiEN/apTwJSzcHU2AnpWVM8WcjChBEEIAABCEAgTcBqGGQDoOf1E4UQXT5VkA1CqpFIq5pnlmZhHo5EgQAEIAABCJg/OqkbBo3JawS8ce3f4pxvQ7SgTA4IQAACEIBAxwRoFjpePKRDAAIQgAAEWhCgWWhBmRwQgAAEIACBjgnQLHS8eEiHAAQgAAEItCDABxxbUCYHBCAAAQgcNYHbd 4etb5Di6NZOPQKkB8CEIAABA5K4ObNmwfN30NymoUeVgmNEIAABCCwGIF79 4tFvtUAtMsnMpKUgcEIAABCBQTOKbfZVAsvqEDH3BsCJtUEIAABCAAgR4J0Cz0uGpohgAEIAABCDQkQLPQEDapIAABCEAAAj0SoFnocdXQDAEIQAACEGhIgGahIWxSQQACEIAABHokQLPQ46qhGQIQgAAEINCQAM1CQ9ikggAEIAABCPRIgGahx1VDMwQgAAEIQKAhAZqFhrBJBQEIQAACEOiRwPo3ON66datH7WiGAAQgAAEIQKABgf8HKhnst0H9Q48AAAAASUVORK5CYII=[/IMG]

"
Windows cannot access \\C01\VideoTVSeries\30 Rock\30 Rock Season1
You do not have permission to access \\C01\VideoTVSeries\30 Rock\30 Rock Season1. Contact your network administrator to request access.
"

Within the /C01/VideoTVSeries/30 Rock folder, user02 **can access** 30 Rock Season06 720p folder and files within that folder fine, but cannot access 30 Rock Season01.

> 
total 1112
drwx------  3 hsiva hsiva   4096 Sep  8 09:26 30 Rock Season01
drwx------  3 hsiva hsiva   4096 Sep  8 09:26 30 Rock Season02
drwxr-xr-x  3 hsiva hsiva   4096 Sep  8 09:26 30 Rock Season03
drwx------  3 hsiva hsiva   4096 Sep  8 09:26 30 Rock Season04
drwxr-xr-x  3 hsiva hsiva   4096 Sep  8 09:26 30 Rock Season05
drwxr-xr-x 23 hsiva hsiva   4096 Aug 20  2012 30 Rock Season06 720p
-rw-r--r--  1 hsiva hsiva 539180 Sep  8 09:26 fanart.jpg
-rw-r--r--  1 hsiva hsiva  49812 Sep  8 09:26 folder.jpg
-rw-r--r--  1 hsiva hsiva  68810 Sep  8 09:26 season01.tbn
-rw-r--r--  1 hsiva hsiva  73119 Sep  8 09:26 season02.tbn
-rw-r--r--  1 hsiva hsiva  76805 Sep  8 09:26 season03.tbn
-rw-r--r--  1 hsiva hsiva  52698 Sep  8 09:26 season04.tbn
-rw-r--r--  1 hsiva hsiva  71805 Sep  8 09:26 season05.tbn
-rw-r--r--  1 hsiva hsiva  69465 Sep  8 09:26 season06.tbn
-rw-r--r--  1 hsiva hsiva  88634 Sep  8 09:26 season-all.tbn
-rw-r--r--  1 hsiva hsiva  10672 Sep  8 09:26 tvshow.nfo


What should I change the value of folders and files so **both user01 and user02 can read files, but only user01 can edit** (write to and delete) for this shared folder?

Is it **safe to change** all the folders within this shared folder **to have drwxr-xr-x**?

**How do I change the value of all the files** in the folder to have this value?


Could someone also explain some these codes, I copied the from somewhere but could not remember where the explanation of it was.

```

[Downloads]
    comment = Downloads
    path = /home/User01/Downloads
    writeable = yes
;   browseable = yes
    valid users = User01

```

**What does browseable = yes** do to that folder on the network?
**What does the ";" at the beginning** of the line do?

I have included the SAMBA file in the post attactments for review those setting up a similar setup[ATTACH]248613[/ATTACH][ATTACH]248612[/ATTACH].

regards
Snooze101

---

### Post by snooze101 on 2013-12-15
Hi,

I found some information about the file permission issue above.

The links below go through in some detail about file permission and ownership setup.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.computerhope.com/unix/uchmod.htm](http://www.computerhope.com/unix/uchmod.htm)

Now that I know how to change the file permission value, could some recommend what should be the 
a) permission for folders and files, that should be only be readable, writeable, excuteable by User01
b) permission for folders and files, that should be readable, writeable, excuteable by both User01 and User02

c) permission for folders and files, that should be only be readable, writeable by User01
d) permission for folders and files, that should be readable, writeable by both User01 and User02

e) What is the difference between have readable access and excuteable access.
e) What is the difference between have readable access and excuteable access for folder and files when accessed over the network.

In the example above, I know the "owner" is User01, the "group" (when using) is plugdev, but what is the "other" category?

regards
Snooze101

---

### Post by Morbius1 on 2013-12-15
That's a lot of questions. Let's start off with some basics:

*** There are two different mechanisms that control what a samba client user can do:
(1) Linux Permissions
(2) Samba Authorizations

You can use one, or the other, or both depending on how you set up the share to accomplish the task. The only requirement is that the Linux permissions must be greater than or equal to the authorizations you set in Samba. If you set the Linux permissions on a shared folder to 777 allowing everyone access but use "valid users = morbius1" in your share definition only morbius1 will have access. If you set Linux permissions to 700 and allow everyone guest access in your share definition no one will have access. The two different mechanisms must cooperate.

***
> Could someone also explain some these codes, I copied the from somewhere but could not remember where the explanation of it was.

[Downloads]
    comment = Downloads
    path = /home/User01/Downloads
    writeable = yes
;   browseable = yes
    valid users = User01

What does browseable = yes do to that folder on the network?
What does the ";" at the beginning of the line do?

"browseable" makes the share visible on the network. It's the default for all shares in samba so that's why it has a ";" in front of it.

*** A note on the following HowTo: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I've become convinced that there is no peer review at that site. From the HowTo:
> To change all the permissions of each file and folder under a specified directory at once, use sudo chmod with -R
```
user@host:/home/user$ sudo chmod 777 -R /path/to/someDirectory
```
Don't ever do that. Doing so will make every single file executable to everyone. A better way:
```
sudo chmod -R a+rwX /path/to/someDirectory
```
[COLOR=#0000cd]Note: That's a big X in rwX[/COLOR]. With that command all folders will be set to 777 and all files will be set to 666 except those that were executable to begin with. Folders need to be set to be executable to be opened to see what's inside but only those files that you want to be executable should be made so.

---

### Post by snooze101 on 2014-01-12
> 
*** There are two different mechanisms that control what a samba client user can do:
(1) Linux Permissions
(2) Samba Authorizations

You can use one, or the other, or both depending on how you set up the  share to accomplish the task. The only requirement is that the Linux  permissions must be greater than or equal to the authorizations you set  in Samba. If you set the Linux permissions on a shared folder to 777  allowing everyone access but use "valid users = morbius1" in your share  definition only morbius1 will have access. If you set Linux permissions  to 700 and allow everyone guest access in your share definition no one  will have access. The two different mechanisms must cooperate.

***


That clears up how samba and linux permissions work, and how to configure Samba to share network folder with window users. Thanks again[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=982144")Morbius1 for your help with setting this Samba network share. This Samba shae is now working, and I will update this thread, and the first post with a summary of how I setup the Samba share.

Regards
Snooze101

---

