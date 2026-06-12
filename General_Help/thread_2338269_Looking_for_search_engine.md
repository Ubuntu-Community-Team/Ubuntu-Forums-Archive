---
title: "Looking for search engine"
date: 2016-09-26
forum: General Help
---

### Post by satimis on 2016-09-26
Hi all,

I have a large database about 120GB.  Most of them are .txt files.  I'm looking for a search engine to be installed on a VM.  On googling I found;

Terrier
[http://terrier.org/](http://terrier.org/)

and

Top 5 Open Source Search Engines
[http://www.mytechlogy.com/IT-blogs/8685/top-5-open-source-search-engines/#.V-lEjLUvASs](http://www.mytechlogy.com/IT-blogs/8685/top-5-open-source-search-engines/#.V-lEjLUvASs)

1. Lucene 
2. Sphinx 
3. Xapian
4. Indri
5. Zettair

Which of them would you recommend?  Or there are any others?

Please shed me some light.  Thanks in advance

Regards
satimis

---

### Post by HermanAB on 2016-09-26
grep

---

### Post by TheFu on 2016-09-26
For a website, I'd use htsearch or e-swish. [https://www.linuxjournal.com/article/6652](https://www.linuxjournal.com/article/6652) - Josh is a friend of mine. ;)

For a desktop or server with local access, I'd use **recoll**.

I actually use both of these today.  Recoll is amazing.  I use it for my media server and document server ... 8+TB.

---

### Post by satimis on 2016-09-26
Hi all,

Thanks for your advice.

Currently I use cat and grep, the Shell commands, for searching but not very convenient.  I'm looking for whether there is a search engine to replace the Shell commands.  If I search for "xxx" it will display all filenames including folders which have "xxx" on them.

This is a PC running Oracle Virtualbox.  All works are done on VMs, keeping the Host clean.  On the Host /home/data/ is solely for storage of documents, the results of all works done.  They are NOT open to public but for my own use only.

Should further information is required, please advise.

Thanks

satimis

---

### Post by TheFu on 2016-09-26
If you just want to search filenames, use locate/updatedb.  THAT is exactly what it is for.  Full text search is a different issue, completely.  

```
$ locate interface

# Case insensitive:
$ locate -i interface

```
Might need to tweak the /etc/updatedb.conf  file - it doesn't do temporary mounts/storage by default. Same for NFS, but you can override either as needed.

---

### Post by satimis on 2016-09-26
> **TheFu said:**
> If you just want to search filenames, use locate/updatedb.  THAT is exactly what it is for.  Full text search is a different issue, completely.  

```
$ locate interface

# Case insensitive:
$ locate -i interface

```
Might need to tweak the /etc/updatedb.conf  file - it doesn't do temporary mounts/storage by default. Same for NFS, but you can override either as needed.
Hi,

I want to search the files including their folders which contain the string "xxx' (for example)

```

grep -R 'xxx' /home/data/

```
find .txt files including their folders which contain 'xxx' 

It also finds .html files which contain 'xxx' including their folders but generating lot of codes which I couldn't understand.

satimis

---

### Post by steeldriver on 2016-09-26
How about

```

grep -R --include='*.txt' 'xxx' /home/data/

```

or

```

find /home/data/ -type f -name '*.txt' -exec grep 'xxx' {} + 

```

---

### Post by satimis on 2016-09-26
> **steeldriver said:**
> How about

```

grep -R --include='*.txt' 'xxx' /home/data/

```

or

```

find /home/data/ -type f -name '*.txt' -exec grep 'xxx' {} + 

```
Both commands work seamlessly.  Thanks

What is the option of {} ?

How to find a string in .pdf and .odt files

satimis

---

### Post by TheFu on 2016-09-27
> **satimis said:**
> Both commands work seamlessly.  Thanks

What is the option of {} ?

How to find a string in .pdf and .odt files

satimis

Use recoll.
or
Use htsearch/e-swish with settings that index pdf and libreoffice files.

Did you read that link I provided? Even skim it?

The answer to the question about 'find' - [https://askubuntu.com/questions/573385/how-to-use-if-inside-exec-attribute-of-find](https://askubuntu.com/questions/573385/how-to-use-if-inside-exec-attribute-of-find)

---

### Post by satimis on 2016-09-28
> **TheFu said:**
> Use recoll.
or
Use htsearch/e-swish with settings that index pdf and libreoffice files.

Did you read that link I provided? Even skim it?

The answer to the question about 'find' - [https://askubuntu.com/questions/573385/how-to-use-if-inside-exec-attribute-of-find](https://askubuntu.com/questions/573385/how-to-use-if-inside-exec-attribute-of-find)

Hi TheFu,

Thanks for your advice.  Sorry for overlooking your posting on #3.  I'll test "recoll" installing it on a VM

A brief googling found following documents:-

1)
How to install recoll on Ubuntu 16.04 (Xenial Xerus)
[https://www.howtoinstall.co/en/ubuntu/xenial/recoll](https://www.howtoinstall.co/en/ubuntu/xenial/recoll)

2)
Python extension for recoll (Python3)
How to install python3-recoll on Ubuntu 16.04 (Xenial Xerus)
[https://www.howtoinstall.co/en/ubuntu/xenial/python3-recoll](https://www.howtoinstall.co/en/ubuntu/xenial/python3-recoll)

3)
Recoll user manual
[https://www.lesbonscomptes.com/recoll/usermanual/usermanual.html](https://www.lesbonscomptes.com/recoll/usermanual/usermanual.html)

4)
Recoll features
[https://www.lesbonscomptes.com/recoll/features.html](https://www.lesbonscomptes.com/recoll/features.html)

5)
Recoll : A Full-text Search Tool for Linux Mint (Ubuntu) 
[https://www.youtube.com/watch?v=kMoN-2Ef6kE](https://www.youtube.com/watch?v=kMoN-2Ef6kE)

6)
Tutorial RECOLL 
[https://www.youtube.com/watch?v=eeVuqsvvUr0](https://www.youtube.com/watch?v=eeVuqsvvUr0)


Hoping that it would be sufficient for me to explore "recall"

satimis

---

### Post by TheFu on 2016-09-28
Or you could just 
```
sudo apt install recoll
$ recoll

```
and make the initial settings what is required, tell it to index stuff, then do searches.  It really isn't that complicated as I recall.  Recoll uses Xapian as the back end. Queries are nearly instantaneous.  Printing them out takes all the time, IME.  Recoll is just the front-end - I use it mainly via CLI, but there is a GUI too. The CLI can be used with a few of options:
```
$  recoll -t -q "$1"
```
the manpage has more.

And don't mix recall and "recoll." Different things. ;)

---

### Post by SeijiSensei on 2016-09-28
If the texts are stored in an SQL database, there's no better choice than [Sphinx]("http://sphinxsearch.com/").  It's incredibly fast and provides excellent results.  It takes a little while to set up, but the results are well worth the effort.

I manage some very active listservers and all the messages are routinely dumped into a PostgreSQL database and indexed with Sphinx.  In one of them with > 100K messages, a keyword search took well under a second.

---

### Post by satimis on 2016-10-01
> **TheFu said:**
> Or you could just 
```
sudo apt install recoll
$ recoll

```
and make the initial settings what is required, tell it to index stuff, then do searches.  It really isn't that complicated as I recall.  Recoll uses Xapian as the back end. Queries are nearly instantaneous.  Printing them out takes all the time, IME.  Recoll is just the front-end - I use it mainly via CLI, but there is a GUI too. The CLI can be used with a few of options:
```
$  recoll -t -q "$1"
```
the manpage has more.

And don't mix recall and "recoll." Different things. ;)

Hi

Yes, you're right.  It is NOT complicate.  Just installed recoll on a VM.  Evoking recoll will start automatic indexing.  Unfortunately all documents/data are on the Host.

This is a PC running Oracle Virtualbox.  The Host is SOLELY for running VMs, with Gnome desktop installed.  All works are done on VMs with the working files saved/stored on the Host.  It can say that the Host is a document server.  The files are retained on categorised folders, examples:-

/home/data/
```

Bakery -> Bread ->
       -> Cake ->
       -> Pudding ->
       etc.
Drinks -> Hot beverage ->
       -> Cold beverage ->
       etc.
Cuisine -> Oven dishes ->
        -> Recipes -> Meat ->
                   -> Fish ->
                   -> Shrimps ->
        -> Pasta ->
        etc.
Music -> Piano ->
      -> Orchestra ->
      -> Songs ->
      -> Instrumental music ->
      etc
etc

```

It is quite systematic.  

I don't use those files daily but when in need.  All daily working documents are posted on websites for easy search and anywhere.  I have more than 20 websites for this purpose.

However when I need a particular file I have to drill down folders and folders.  How to save the effort of drilling down folders is my idea to find a search engine OR a way to easy my job.

Regards
satimis

---

### Post by TheFu on 2016-10-01
So is this solved? Please mark it so in the thread tools.

---

### Post by coldraven on 2016-10-01
Maybe you need one these beauties !!! :)
**A Raspberry Pi Hadoop Cluster with Apache Spark on YARN: Big Data 101**


[https://dqydj.com/raspberry-pi-hadoop-cluster-apache-spark-yarn/](https://dqydj.com/raspberry-pi-hadoop-cluster-apache-spark-yarn/)

---

### Post by SeijiSensei on 2016-10-02
> **satimis said:**
> However when I need a particular file I have to drill down folders and folders.  How to save the effort of drilling down folders is my idea to find a search engine OR a way to easy my job.

If all you want to do is identify the locations of files by their names, or their "globs," you can simply use the "locate" command.  For instance, "locate Oz" would bring up the path to the file "Wizard_of_Oz".  It's nearly instantaneous because it uses a database.  See "man locate" and the script /etc/cron.daily/mlocate which rebuilds the database each day.  You can also update it manually by issuing the command "sudo updatedb".

---

### Post by satimis on 2016-10-03
> **TheFu said:**
> So is this solved? Please mark it so in the thread tools.
No.

On terminal start xman
```

&#10219; xman
Warning: locale not supported by Xlib, locale set to C
Warning: Cannot convert string "-*-helvetica-medium-r-*-*-*-120-*-*-*-*-*-*" to type FontStruct
Warning: Cannot convert string "-*-courier-medium-r-*-*-*-120-*-*-*-*-*-*" to type FontStruct
Warning: Cannot convert string "-*-courier-bold-r-*-*-*-120-*-*-*-*-*-*" to type FontStruct
Warning: Cannot convert string "-*-courier-medium-o-*-*-*-120-*-*-*-*-*-*" to type FontStruct
Warning: Cannot convert string "-*-symbol-*-*-*-*-*-120-*-*-*-*-*-*" to type FontStruct
......

```

-> Help
On the its window
Options and Sections 
Options -> Display Directory/Display Manual Page/Help/Search/Show Both Screen 
all grey-out

&#10219; apt-cache policy language-pack-en-base```

language-pack-en-base:
  Installed: 1:16.04+20160627
  Candidate: 1:16.04+20160627
  Version table:
 *** 1:16.04+20160627 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
        100 /var/lib/dpkg/status
     1:16.04+20160415 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu xenial/main i386 Packages

```
language-pack-en-base already installed

&#10219; locale -a```

C
C.UTF-8
en_AG
en_AG.utf8
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_IN.utf8
en_NG
en_NG.utf8
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZM
en_ZM.utf8
en_ZW.utf8
POSIX

```

satimis

---

### Post by TheFu on 2016-10-03
Is this a question?
What does xman have to do with searching files? Perhaps a different thread is needed along with some background?

---

