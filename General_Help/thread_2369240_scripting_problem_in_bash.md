---
title: "scripting problem in bash"
date: 2017-08-20
forum: General Help
---

### Post by alex346 on 2017-08-20
Hello


I would like to make a script which will get the line from file list (ex. passkey) and put it into further processing. 
The main problem is that lines, in text file contains all specials characters, and whitespaces too, as these that was used as a extremmaly-safe passwords. I have written my passwords to .7z files on long list, but I can't find which one is propper for specific .7z file. So i am expecting "password" string and getting it line-by-line from passkey list and later each line into next 7z spawns.


Unfortunately bash stopping the run when first special character occurs on the list, and script trying to load it, going to problem




So I have created two scripts:
which I am calling ~/whiler /path/file.7z


1. 'whiler' 
 1 while read line ; do
 2 echo "$line"
 3 time  expect ~/2.exp $1 "$line"
 4
 5 done<~/passkey.txt
 
 
 2. and the expect cmdfile:
 
  1 #!/usr/bin/expect
 2 set filename [lindex $argv 1]; # Grab the first command line parameter
 3 set passkey [lindex $argv 2]; # Grab the 2nd command line parameter
 4 set timeout 1
 5 spawn 7z t $filename
 6 expect "password:"
 7 send "$klucz\r";
 8 interact
 
 I also tried to make password list in doublequotes (") each line.
 
 What can I do to use strings from file bypassing the injection bash ? Or maybe my scripts are bad?
 
 Thanks for any help

---

### Post by TheFu on 2017-08-20
Normally for automatic remote logins, using ssh-keys is the current preferred method.  It isn't always possible, but .. 
Is there a reason that a F/LOSS password manager isn't a better choice?  Something like keepassx?  It is cross-platform and the encrypted DB files can be shared across all those platforms.

I haven't seen expect used much the last 20 yrs. Good on you for going old-school!

Anything around passwords has many subtle security conditions.

---

### Post by alex346 on 2017-08-21
thank you for your reply,


My sitution is slightly other


I have colleciting lot of archives over the years and when I have created the archive, I have wirte the key/pass [to that archive] to specific xls file. Next, I have load it into BD disc and next hold it in safe place.


And now, after years I see, that I havent propperly saved the keys for few archives. Archives are OK - that is possible to check if file are all in set, but I need to type proper key from my 1000+ records list. And I dont know which one is OK. So, I would like each one,  line by line, in ubuntu terminal, where I have 7zip installed and  available from CLI.


So I have used expect.


Of course, I know that is not secure - keeping all in one xls file. I know.  But that is my personal archive.

---

### Post by TheFu on 2017-08-21
Ah.  So you want an automatic way to de-ZIP each with a specific passphrase that is unique to each.

7z supports passing the password on the command line according to the manpage. That means no need to use *expect*.

So if the file with all the passwords can be made into a CSV or TSV (tab), with the archive-name{tab}passphrase, you can trivially parse that and directly use the password as an input into the **7z e -p** command, right?
Then just check the return code from the 7z command to see if it is non-0 (zero) before moving on to the next possible passphase to test.

An aside ... 
BTW, for ZIP archives, there are brute force password cracking tools which allow a "custom DB" to be used for attempts.  I haven't looked, but there are probably versions for 7z.  I haven't looked for these things in years.  I find it easier to keep these things in a password manager with an appropriate identifier.   Google found this: [https://sourceforge.net/projects/sevenzcracker/](https://sourceforge.net/projects/sevenzcracker/).  The ZIP cracker I used in the 1990s was capable of billions of attempts per second on THAT hardware.

Interesting problem.  I'd probably use perl, but that's more about my limitations with bash and know how to trivially parse a file in perl using the 'split' built-in.  Looks like about 5-8 lines of perl. ;)   <--- had to add this.

#     Perl pseudo-code [these would be my initial comments]
# read the entire password file into an array. @pass=<>;
# Loop over all 7z archives, while {globbing}
# use whatever pattern matching you can to limit which of the password file entries should be attempted
# try the passphrase - if rc is 0, fine ... move onto the next archive - I would print the filename and passphrase
# rc != 0, keep trying passphrases until no more exist - print out failure for archive/filename.

Of course, this all assumes that my understanding of 7z password use is correct. The 7z manpage:
```
       7-Zip returns the following exit codes:

              0      Normal (no errors or warnings detected)

              1      Warning (Non fatal error(s)).  For  example,  some  files
                     cannot  be read during compressing. So they were not com&#8208;
                     pressed

              2      Fatal error

              7      Bad command line parameters

              8      Not enough memory for operation

              255    User stopped the process with control-C (or similar)

```

Basically, the output from my script would be something like:

```

file0001.7z{tab}padfaskl34512483rewufa(*&*TYG%%^TUG
file0001.7z{tab}krk234rfsdjala8%$%^$%^$%^asdf3k4ewkkasd
....
file01999.7z{tab}FAILED
....
file1324234.7z{tab}One (1) stupid password.
```

Then I would feed those into keepassx for any future needs. Any characters should be fine in the passphases, including a tab.  

I used to keep my hundreds of passwords inside an XLS too. ;)   And after you get each archive and passphrase known, use something like [https://github.com/jamesls/python-keepassx](https://github.com/jamesls/python-keepassx) or [http://kpcli.sourceforge.net/](http://kpcli.sourceforge.net/) for a CLI interface into the encrypted DB.

---

### Post by alex346 on 2017-10-30
Thank you for your reply, sorry for my late reply, I still have that problem, but I was offline few weeks.
Thank you for hints with encrypted DB - my xls was made due to fast needs in past. And later never changed. So, now I have effects :(

I have to make small correction - for me doesn't matter the input or output files type. I also can analyse the output on the console and grep any pattern, when the 7z starts to work - with unpacking.

Your solution is what I need, I suppose. But I am very beginner in bash, I don't have used python nowhere. I don't know how can I use it.

Will the python vars allow to avoid interpreting long keys by bash? The problem is that keys have different length, quantity and position of special characters.

Would be possible to smile to you for any small example what can I test further? 

best regards

---

### Post by TheFu on 2017-10-30
Sorry. I don't know python.   

There are lots of programming tutorials for both python and bash on the internet.

Python is a general purpose language capable of pretty much anything.  This sort of problem would be easily solved in python, perl, ruby, go, or any other fully-capable, scripting language.  I wouldn't do it in bash, but bet some admins who script in bash daily, for years, would.

Some people here are happy to help, if you post some code.  The attempt is VERY important.

---

