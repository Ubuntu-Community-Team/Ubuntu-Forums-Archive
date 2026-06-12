---
title: "Howto edit a .DB file?"
date: 2020-08-27
forum: General Help
---

### Post by aboka on 2020-08-27
hi, im using Ubuntu 20.04 LTS and i hv a .DB file install together with a program, but could not find ways to edit them. First i try download the file into my Windows and use MS Access and DB Browser for SQLite to try open it, but both also not working. so i think maybe just do it inside Ubuntu. By searching online, i learn that we need to find out the type of file then only find the way to edit them. 

Here is the code i run and the result. It doesn't give much info on what file/db is that. Please advice. Thank you,

p/s - i dont mind if the solution use Windows or Ubuntu, just like to open and edit them

```

root@v2ray:# file userinfo.db
userinfo.db: data

```

'Error Msg'
DB Browser for SQLLite give error: file is not a database
MS Access: Unrecognized database format

The program name is Cloak. It is a plugin for Shadowsocks. And there is no info on their github pages

---

### Post by TheFu on 2020-08-27
File extensions don't matter on Unix systems. They are for humans and not always correct. There are hundreds, if not thousands, of different DB file formats. Not all are standardized. The programmer can make anything up she wants and call it a "DB".

For example, **man db** or **man dbopen** or **man hash**.  

So, you'll need to figure out the file contents.  Perhaps look at a Berkley DB type of DB file? [https://web.stanford.edu/class/cs276a/projects/docs/berkeleydb/ref/intro/dbis.html](https://web.stanford.edu/class/cs276a/projects/docs/berkeleydb/ref/intro/dbis.html)  Could be anything.  There may not be any DB browser, just the program written for that specific file, which can access the ".db".  I've used ctree libraries for this many times or Sleepycat or Raima or ... a simple CSV perl module.  Just depends on what was needed.  

SQLite can be overkill for many needs and isn't without some problems.

I looked through the installer [https://github.com/cbeuw/Cloak#quick-start](https://github.com/cbeuw/Cloak#quick-start) and didn't see any clues for the DB.  At that point, getting any libraries and using dev tools to uncover external dependencies using **nm** and **strings** would be my next step.

---

### Post by ActionParsnip on 2020-08-27
Where did you get the file from? What made the file?

---

### Post by aboka on 2020-08-27
@TheFu, it seems like too advance for me, but none the less will check out the link. thanks :)

@ActionParsnip, it got it from one of its fork project. here is the main project - [https://github.com/cbeuw/cloak](https://github.com/cbeuw/cloak) cant find much info on both of their pages for the .db file

p/s - i did post question there, but its not relate to this as post earlier. still waiting for someone to reply(soon) and so hopefully i could ask about this too

cheers,

---

### Post by aboka on 2020-08-27
p/ss- i open up the file using text editor on Windows as some ppl say the 'top part' will contain some info of what kind of database it is. but all i see is just gibberish and its Field Description:

Top 1st line - '               íÚí                                              $NÂ¾§-¹   '

'Field Description' - 'DownCredit   o    ê&#8226;DownRate        ExpiryTime    dm¼fSessionsCap   UpCredit   püb&#8211;UpRate '

And lotsa whitespaces everywhere

---

### Post by TheFu on 2020-08-27
> **aboka said:**
> p/ss- i open up the file using text editor on Windows

This alone can be very dangerous.  Windows editors used to have a bad habit of changing the end-of-line character which will break binary files. I don't know which, if any still do that.  When you don't want to modify a file, use a "viewer", not an editor!

**more**, **less**, **view** are the common Unix programs for that.  more and less are also called "PAGERS".  **less** has more features than more.  Those crazy unix people with their jokes.

Because you knew to run 'file', I assumed a more advanced user. Sorry.
Strings (really 'strings') is a handy file to run against non-compressed data. Most DB files are non-compressed so multiple processes can access records concurrently, but safely.

Does "golang" have a default DB type they like to use?  That would be where I started. If the coders are long-time Unix people, they might choose BerkleyDB or something very similar, like the GNU version of it. Usually, those are key-value DBs with 1 key and 1 value per file. We can think of them like columns, but that isn't really the organization internally.

The question I asked the project would be would be "does X project use a standard or embedded DB? If so, which one?"

---

### Post by aboka on 2020-08-27
@TheFu - this the results:
less will ask this '"userinfo.db" may be a binary file.  See it anyway?' then 'y' will show first line: ^@^@^@^@^@^@^@^@^D^@^@^@^@^@^@^@<ED><DA>^L<ED>^B^@^@^@^@^P^@^@^@^@^@^@^D^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^E^@^@^@^@^@^@^@^F^@^@^@^@^@^@^@<FC>^@^@^@^@^@^@^@P<FB>=((X<E4>

more produce nothing/'black screen' 

view -
first lline: ^@^@^@^@^@^@^@^@^D^@^@^@^@^@^@^@íÚ^Lí^B^@^@^@^@^P^@^@^@^@^@^@^D^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^E^@^@^@^@^@^@^@^F^@^@^@^@^@^@^@ü^@^@^@^@^@^@^@Pû=((Xä<8e>^@^@^@^@^@^@^@^@^

last line: "userinfo.db" [readonly][noeol][converted] 5L, 32812C

well, just hope they will reply me soon so could ask about this. will update you ppl if i got anything, thanks :)

p/s - will try ask them this '[COLOR=#000000]"does X project use a standard or embedded DB? If so, which one?"[/COLOR]

---

### Post by dinkidonk on 2020-08-28
> **TheFu said:**
> File extensions don't matter on Unix systems. They are for humans and not always correct.

That's not entirely true.. Content examination is more like a fall-back in most modern distributions, the caches/databases containing information about mime types are "compiled" from XML files found under /usr/share/mime and ~/.local/share/mime etc. The XML files define a content type linked to one or more glob patterns (file extensions with wildcards like "*.txt"), a textual description of the file type and maybe an icon to go with it.

---

### Post by Holger_Gehrke on 2020-08-28
After getting the source and doing a lot of 'grep'-ing I can tell you that it's a [bolt]("https://github.com/boltdb/bolt")-database.

Holger

---

### Post by aboka on 2020-08-28
> **Holger_Gehrke said:**
> After getting the source and doing a lot of 'grep'-ing I can tell you that it's a [bolt]("https://github.com/boltdb/bolt")-database.

Holger

hahah you got the jackpot correct ;) i was about to post the finding as one of their creator has reply and say the same thing - [COLOR=#24292E][FONT=-apple-system]The database is created using an engine called [/FONT][/COLOR][bbolt]("https://github.com/etcd-io/bbolt")

Thanks a lot guys for all the tips and advice :)

---

