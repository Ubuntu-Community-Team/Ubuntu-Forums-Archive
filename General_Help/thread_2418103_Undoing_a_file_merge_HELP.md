---
title: "Undoing a file merge HELP"
date: 2019-05-01
forum: General Help
---

### Post by mickwombat on 2019-05-01
I was trying to automatically append a file extension to a bunch of file in cli and made a slight (very big) mistake.  I've done many times before but tiredness overcame me on this occasion.

Was using this

```
for i in *; do mv "$i" "$i.pcapng"; done
```

and got the syntax wrong.  What I have left is one giant file that has merged everything together, including the non wireshark files.

I can only hope that it just concatenated the raw data together, so is there any way I can edit this file and just delete out the bits?  Orginally I had about 13 x 100meg pcaps, some text files, dmg, mp4 and so on.  Would like to get at least my pcaps back...even if it is one big file.

Any advice appreciated.

Thanks

---

### Post by Impavidus on 2019-05-01
First make a backup of your concatenated file to make sure you don't do more damage during your recovery efforts. Having backups of some of the concatenated files would help too, not only because you no longer have to extract them from your merged file, but also because that tells you the boundaries of it's neighbours.

If you know the exact sizes of the files (from a previous ls -l output for example) it's not so hard.

```
# To copy the last n bytes to a different file:
tail -c <n> bigfile >newfile

# To copy the first n bytes to a different file:
head -c <n> bigfile >newfile

# To copy all but the last n bytes to a different file:
head -c -<n> bigfile >newfile

# To copy all but the first n bytes to a different file:
tail -c +<n+1> bigfile >newfile
```
Replace <n> or <n+1> with the number of bytes or the number of bytes plus one and substitute appropriate filenames.

If you don't know the exact sizes, it will get a bit more difficult. Some file formats tell somewhere near the beginning of the file how long the file is supposed to be (usually in binary), some tools may tell you they found x bytes of garbage at the end of the file, suggesting those x bytes belong to other files, plain text files contain only valid UTF-8 encoded text ending with a newline character, so if you know what file formats you're looking at and you can deal with text editors and maybe a hex editor, it can be fixed. No standard recipe though. If two text files are concatenated, you can only tell from the contents.

---

### Post by TheFu on 2019-05-01
split and join might be useful.

If the first and/or last line of the original files is known, you can use grep to find the line number and then split on the specific lines.

---

