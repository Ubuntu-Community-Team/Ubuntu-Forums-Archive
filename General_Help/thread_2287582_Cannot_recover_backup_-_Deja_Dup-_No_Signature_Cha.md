---
title: "Cannot recover backup - Deja Dup- No Signature Chain"
date: 2015-07-20
forum: General Help
---

### Post by tom195 on 2015-07-20
I was in the middle of backing up my hard drive to an external drive when my power supply was interrupted. I foolishly forgot this happened and that my back up was not compete before reinstalling Ubunutu on the main hard drive. I wiped out all my files only to remember my back up was not complete. When I try to restore from the backups section in system settings, no restore file can be found. When I use Terminal and duplicity list-current-files it reports this:
```
tom@Evermind:/media/tom/Orb$ duplicity list-current-files file://media/tom/OrbLocal and Remote metadata are synchronized, no sync needed.
Last full backup date: none
Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1494, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1488, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1337, in main
    do_backup(action)
  File "/usr/bin/duplicity", line 1426, in do_backup
    list_current(col_stats)
  File "/usr/bin/duplicity", line 671, in list_current
    sig_chain = col_stats.get_signature_chain_at_time(time)
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 977, in get_signature_chain_at_time
    raise CollectionsError("No signature chains found")
CollectionsError: No signature chains found
```

The only files I can see on the external drive are named "duplicity-full.20150717T103159Z.vol1.difftar.gpg," increasing in volume number.

I fear I may have lost all my data...
Please, if anyone can help it would be MUCH appreciated!

---

### Post by ochoadavid on 2015-07-27
Dear Tom:
I was having a similar problem and, finally, manage to solve it. 

Note: I'm using a ssh backend, and I'm not sure that this solution will work in any backend (S3, file, etc.)
Note2: It could be a good idea to make a backup of all the files (in your disk and in .cache/deja-dup/) before trying this out.

I tried a lot of things, but I'm thinking two of them were the ones that solved this problem:
- First I installed python-paramiko (somewhere the software was complaining about don't having it). I used *aptitude*, but *apt-get install paramiko* should work as well.
- After installing that package, i discovered that the last files in the backup archive (should be three two with "*inc*" ending in *manifest.gpg*, *vol1.difftar.gpg* and one more "*new-signatures*" ending in *sigtar.gpg*) were all them zero sized. I just deleted them and the software started running normal. All the files have the sequence  <year><month><day>T<time>.to.<year><month><day>T<time>.  Be careful to only erase the newer ones.

If those last files aren't zero sized try also checking them. If they are ok, you should be able to un-gpg them using the command "*gpg filename*". This command should ask for your passpharse and produce an ouput file (with the same name but w/o the *.gpg* part of the extension).

Some files can be also in ~/.cache/deja-dup/<a seemly random sequence of numbers and letters>, although I'm not sure how to check them.

In less words: the duplicity incremental system allows -but do it carefully- to erase the last incremental backups if there is a problem in them and the rest of the information may be undamaged.

David

---

### Post by alanfranz2 on 2016-04-21
Hello,
this thread is quite old, but I'm answering BTW if anybody else happens to experience the same error.

The problem lies in your file url. It should have three slashes - file:/// - not just two, which makes sense for a file URL (which should have either one or three in fact).

---

