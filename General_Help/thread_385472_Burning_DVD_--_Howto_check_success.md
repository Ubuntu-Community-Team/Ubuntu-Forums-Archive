---
title: "Burning DVD -- Howto check success?"
date: 2007-03-15
forum: General Help
---

### Post by graabein on 2007-03-15
I have been having problems with my DVD-writer. Have been getting some aborted burn sessions in gnome baker. So when I finally get a successful burn, how do I know that it is 100% okay? That every file is burned correctly?

And how do I run a check on the target directory to check the files before I start burning? 

It's my photo collection that I'm trying to backup and it would be disaster if I'd lost everything. I keep a copy on a separate hd but it would be nice to have backups on DVD as well.

---

### Post by taurus on 2007-03-15
Try using k3b.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install k3b
```

---

### Post by graabein on 2007-03-15
I don't want lots of KDE libs on my system just to burn DVD's but thanks for the suggestion.

---

### Post by taurus on 2007-03-15
Graveman is another option.

---

### Post by gus sett on 2007-03-15
**return visit** OK. a search on nec 3500 brought up a list of colleagues. So
what % of burns do you consider successful?
this may be somewhat rudimentary, but you can compare filesystem information
using Linux's native *diff* command.  Syntax etc. is available in *man*.

:?: How often do you have a successful burn
:?: What DVD capacities and brands do you use
:?: What is the model, age, and speed of your drive

> **graabein said:**
> I have been having problems with my DVD-writer. Have been getting some aborted burn sessions in gnome baker. So when I finally get a successful burn, how do I know that it is 100% okay? That every file is burned correctly?

And how do I run a check on the target directory to check the files before I start burning? 

It's my photo collection that I'm trying to backup and it would be disaster if I'd lost everything. I keep a copy on a separate hd but it would be nice to have backups on DVD as well.

---

### Post by graabein on 2007-03-15
I'll post the info tomorrow. Good night.

---

### Post by Adler on 2007-03-15
Hi All,

And, I don't mean to hi-jack this thread. But, I 've never figured out how-to burn my complete music collection across multiple DVDs. Basically, SPAN disks. 

Any burners out there? 

Adler

---

### Post by kpkeerthi on 2007-03-15
Adler, 
I would advice you to post a new thread. You'll likely get more response that way.

---

### Post by Adler on 2007-03-15
kpkeerthi,

Thanks for that. 

Adler

---

### Post by SuSUntu on 2007-03-16
Without getting into the whys and wherefores of your burning issues (was that a pun?), I would (and do) test integrity using the **md5sum** command. **

'md5sum' does not natively do recursion through subdirectories, so you'll need to pipe the information to 'md5sum' from another command that does (note: some other tools like 'md5deep' do recursive traversal through subdirectories, but it is not a default Ubuntu application). For example, this command using 'find' and 'md5sum' works just fine:

```

 find /DirectoryOfFilesToBeBurned -type f  -print0 | xargs -0 md5sum > /DesiredLocationOfMd5SumOutput/myfiles_dvd01.md5

``` 

The above command will:

- recursively find all files of type "file" (as opposed to '-type d' which is directory) in the path, /DirectoryOf FilesToBeBurned;

- it will pipe all found ../relativepath/file(s) to 'md5sum' to calculate the MD5 hash(es);

- it will output the results of 'md5sum' to the file of your choice (e.g., /DesiredLocationOfMd5SumOutput/myfiles_dvd01.md5)

- the additional arguments in that command line (-print 0, xargs, [xargs] -0) "assure" that each subsequent command receives its input properly formatted.

Once you have the file "myfiles_dvd01.md5", you can burn that to your DVD along with your photos, and then check everything after the burn process by issuing this command (you can also test the results against the files on your HDD before you burn them if you like, you'll just simply need to adjust the paths in the command below):

```

find /PointToDVDMedia/DirectoryOfFilesThatWereBurned -type f  -print0 | xargs -0 md5sum -c /PointToDVDMedia/myfiles_dvd01.md5 > /DesiredLocationOfMd5SumOutput/myfiles_dvd01_md5check_results.txt

```

**Additional Info**:

I've already mentioned that 'md5sum' does not do recursive directory traversals, but that was taken care of via piping output from the 'find' command. However, you also need to be aware that the output of 'md5sum' (whether to a file or the terminal) will look like this:

```

calculatedmd5sum ./relativepath/file

```

The relative path is the important feature here.

For example, the contents of 'myfiles_dvd01.md5' may look like this:

```

1jdh55sdffsf455sfsdf545sdf5sdf4a  ./Source/keepass/KeePassX-0.2.2.tar.gz
2jdh545sdffsf455sfsdf545sdf5sdf6  ./Debs-Created/glipper_0.95.1-1_i386.deb

```

When 'md5sum -c' is run using the file containing the above info (myfiles_dvd01.md5 in our example code), it will report one of the following about each file (the info will be appended after the name of each file):

- : OK       #My comment:  new md5 calculation matches original md5sum in 'myfiles_dvd01.md5'

- : FAILED   #My comment:  new md5 calculation does not match original md5sum in 'myfiles_dvd01.md5'

- : FAILED open or read    #My comment:  a ./relativepath/file in 'myfiles_dvd01.md5' was not found amongst the ./relativepath/files being checked on the DVD

The most important thing to be aware of, and which is my point here, is that if you copy the files to the DVD into paths that differ from the relative paths originally stored in 'myfiles_dvd01.md5', you won't see any output at all. So, for example, if you have a 'myfiles_dvd01.md5' file containing:

```

1jdh55sdffsf455sfsdf545sdf5sdf4a  ./Source/keepass/KeePassX-0.2.2.tar.gz
2jdh545sdffsf455sfsdf545sdf5sdf6  ./Debs-Created/glipper_0.95.1-1_i386.deb

```

but you copied / burned the files onto the DVD as:

```

./keepass/KeePassX-0.2.2.tar.gz
./glipper_0.95.1-1_i386.deb

```   

''md5sum -c' would run with no results as it ignores as irrelevant any files not in the list of files to check contained in 'myfiles_dvd01.md5'.

Bottom line: maintain the same directory structure below the root / starting directory on your DVD as you had on your HDD. If this is not workable, say you wanted to copy all your files to the root of the DVD even though they were in subdirectories on your HDD, you have options such as:

- copy your files to a temporary directory on the HDD which simulates the structure you would like to use for the DVD, then use md5sum to calculate the hashes against that structure;

- pipe the output of 'md5sum' through an additional string manipulation command to alter it to your desires (e.g., you could remove the ./relativepath info from the output leaving only the file name in the case of a DVD where all files originally in subdirectories were being copied / burned to the root of the DVD).

Finally, you could elaborate on the above commands by adding pipes to 'grep' which would, for example, summarize the output of 'md5sum -c' showing only truly FAIL'd md5sums, ignoring files with status "OK" and "FAILED open or read" (e.g. piping output of 'md5sum -c' through **grep 'FAILED$'**

-------------

** Note:
 
Warning - Editorial: I still don't trust the available Gnome burning tools  (more likely a prejudice on my part but founded in some reality). Though I've had no complaints with limited use of K3B, I, like you, don't favor adding the KDE stuff just for that application. So, egad!, I do my DVD burning in Windows using a long-time trusted friend, Nero. I also have other resources available to ensure peace of mind about burns (like KProbe2), so I just "feel" more confident using the tools available in Windows. By the way, even in burning apps (including Nero) that allow for automatic integrity checks at the end of a burn, I still use md5sum tools to create *.md5 files which I place permanently on the CD / DVD (i.e., I forgo entirely the use of the built-in integrity checkers).  If you really want to be hardcore, you could use parity volume tools, but I'm not that hardcore.

-----------
Sorry for the inordinately long post for something that is relatively simple.

---

### Post by graabein on 2007-03-16
> **gus sett said:**
> this may be somewhat rudimentary, but you can compare filesystem information
using Linux's native *diff* command.  Syntax etc. is available in *man*.

:?: How often do you have a successful burn
:?: What DVD capacities and brands do you use
:?: What is the model, age, and speed of your drive

From **lshw**:
*-cdrom:1
product: _NEC DVD_RW ND-3500AG
physical id: 1
bus info: ide@1.1
logical name: /dev/hdd
capabilities: packet

It is max 4-5 years old or... I don't know... I think it's newer but I can't really remember. I usually go for Verbatim DVD's and the drive is said to be +/- but I can't remember what type I use. 4,7GB DVD+R works the best I think... Speed of drive is maybe 8x? But I usually burn at 4x or even 2x. 

Thanks for the **md5sum** tip SuSUntu. I thought something along those lines but I've never looked into it. I'll definitely check it out and read your post twice. ;-)

---

