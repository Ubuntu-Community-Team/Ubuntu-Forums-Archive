---
title: "Command to find public IP address"
date: 2020-09-22
forum: General Help
---

### Post by satimis on 2020-09-22
Hi all,

On Terminal run;

$ dig +short myip.opendns.com @resolver1.opendns.com```

223.17.36.90

```

Whether 223.17.36.90 is the public IP address allotted by ISP ?

Are there any other commands ?

Thanks

Regards

---

### Post by HermanAB on 2020-09-22
Type one of these into your browser:
showmyip.com
whatismyipaddress.com
etc.

---

### Post by ajgreeny on 2020-09-22
You can use curl in terminal to get a lot of this info.
```
curl  ipinfo.io/ip
{
  "ip": "95.149.108.51",
```
If you want more detail omit the final ***/ip*** in the command and you will get
```
~$ curl  ipinfo.io
{
  "ip": "95.149.108.51",
  "city": "xxxxxxxxx",
  "region": "England",
  "country": "GB",
  "loc": "lat-long",
  "org": "AS12576 EE Limited",
  "postal": "post-code or zip code",
  "timezone": "Europe/London",
  "readme": "https://ipinfo.io/missingauth"
```
Note; I have deleted all the detailed location info about my location shown here but it was all 100% correct.

---

### Post by TheFu on 2020-09-22
Be aware that this:
```
$ curl  ipinfo.io/ip
```
can be incorrect for the location data.  For mine, it is about 40 miles wrong.  The closest I've ever seen any of these geolocation services was 2 miles, but usually they are 10-40 miles off.

Your router knows the IP, so you could ask it. There are script for many routers that do exactly that.  **ddclient** is what I used before getting static IPs.

OTOH, using curl to drop the IP somewhere every hour if you don't need to update a DNS setting, is what I'd do. 
If you need this for updating DNS, I'd use ddclient.

Just depends on the need.

---

### Post by scorp123 on 2020-09-22
> **satimis said:**
> Are there any other commands ? 

All of these work:

```

wget checkip.amazonaws.com -O - -q
wget eth0.me -O - -q
wget ifconfig.me -O - -q
wget ipinfo.io/ip -O - -q
wget icanhazip.com -O - -q

```

---

### Post by satimis on 2020-09-22
Hi all,

Lot of thanks for your advice.

showmyip.com

recommended by HermanAB above is easy to remember.  Thanks

Regards

---

### Post by TheFu on 2020-09-23
Why remember anything?

Put it into a script in your ~/bin/.
Or make an alias "get-ip-pub" - and add it to your shell's aliases.  May have a "get-ip-lan" alias too.

---

### Post by satimis on 2020-09-24
> **TheFu said:**
> Why remember anything?
Hi,

Thanks for your advice.

It is my headache, having a huge database with files accumulated in >15years.  They are assorted in folders, most .txt files.  Each time when looking for a specific document I have to searching through the folders.

I'm aware that there is a shell script which can do the job searching for a document with "abc" contents.  Unfortunately I forgot it.  Is it "Find" command?

Can you help?  Thanks.

> 
Put it into a script in your ~/bin/.
Or make an alias "get-ip-pub" - and add it to your shell's aliases.  May have a "get-ip-lan" alias too.
Still I have to remember the name of the script, similar to showmyip.com

Regards

---

### Post by TheFu on 2020-09-24
I keep personal files in 2 places.  One for scripts and the other for notes.  When creating those files, I add in comments with all sorts of search terms, since I learned 30 yrs ago, if I can't find it later, that work is effectively lost.

When I need to remember how to do something from last week, last month, last year, last decade, or 1992, I'll use grep in one of those directories using minimal terms.
```
$ egrep -i win10 *
Old_CIFS_Mounts: protocol = SMB2 ; for Win10 and Linux clients
Win10-n-Samba.txt:Win10 disables NetBIOS and using a manual CIFS is necessary.
```
The answer is in one of those files.

I have some RAID setup and troubleshooting scripts/notes, but I can never remember the name exactly. I know the command used is mdadm.
```
$ egrep mdadm *
bootinfoscript:#   Only works if "mdadm" is installed.
bootinfoscript:if [ $(type mdadm >> ${Trash} 2>> ${Trash} ; echo $?) -eq 0 ] ; then
bootinfoscript:  MD_Active_Array=$(mdadm --detail --scan | ${AWK} '{ print $2 }');
bootinfoscript:  mdadm --assemble --scan;
bootinfoscript:  MD_Array=$(mdadm --detail --scan | ${AWK} '{ print $2 }');
bootinfoscript:    [[ "${MD_Active}" -eq 0 ]] && mdadm --stop "${MD}";
grep: kmttg: Is a directory
**md1-raid-create.sh**:# sudo mdadm -C $RDEV --chunk=256 --level=raid1  --raid-devices=2 $DEV1 $DEV2
md1-raid-create.sh:# sudo mdadm --assemble $RDEV  $DEV1 $DEV2
grep: mikogo: Is a directory
grep: nxclient: No such file or directory
grep: RCS: Is a directory
```

Ok, md1-raid-create.sh is the file I want.

When I'm scripting, it is common to need an input filename so I can create a few different output files based off it.  I almost always call this variable ROOT.  Over the years and with different shells, I've needed to set this value a few different ways.  Bash makes it easy, provided we know the filename pattern.
Say the input is "foo-file.name.avi"
```
ROOT="${filename%.*}"
```
would set ROOT to "foo-file.name" which is handy. If the input file doesn't have an extension, something else would need to happen. Another method for Borne Shell:
```
ROOT=`echo $1 | sed -e 's/.avi//g'` 
```

Just depends on what I need.

---

### Post by ajgreeny on 2020-09-24
I use the curl command I mentioned in post #3 in my conky configuration  file so the conky display on my desktop shows that along with a lot of other system other  system information such as ram usage, network upload and download speed, current cpu usage and the processes  using each core, plus a lot of other useful info..

---

### Post by satimis on 2020-09-26
Hi all,

Lot of thanks for your advice.  

I'll start another posting;
How to search my database

Regards

---

