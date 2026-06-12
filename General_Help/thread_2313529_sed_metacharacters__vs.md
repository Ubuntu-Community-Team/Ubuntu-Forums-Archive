---
title: "sed metacharacters * vs ?"
date: 2016-02-13
forum: General Help
---

### Post by TaiChiRabbit on 2016-02-13
Hi
I am writing a bash shell script to tidy up the file names of some tv shows and wanted to use SED to extract the series and episode within each file name. Some of the files have a dot between the series and episode, sometimes there is no dot, eg:
TVSHOW title1 S09.E12.mp4
TVSHOW title2 s09e12.mp4

The script below works fine, but is a bit overkill since it will find zero or 100 dots between the series and the episode:
```
foo=$(echo $oldfilename|sed -n 's/^.*[Ss]\([0-9][0-9]\)\.*[Ee]\([0-9][0-9]\).*/S\1E\2/p')
```
will return foo=S09E12


However I'm just wondering why the following script doesn't work (it returns an empty string), which uses the more appropriate '?' and should capture only zero or one dot between the series and episode, rather than  '*'.  I ran it through an online regex tester and it worked [without the backreferences so maybe they are the issue?], so am curious why it doesn't work in the real world!
```
foo=$(echo $oldfilename|sed -n 's/^.*[Ss]\([0-9][0-9]\)\.?[Ee]\([0-9][0-9]\).*/S\1E\2/p')
```

Thank you

I'm using Ubuntu 15.10

---

### Post by mcgess on 2016-02-13
Hi

You could try using the -E option to sed which enables extended regular expressions
A command like
```
foo=$(echo $oldfilename|sed -n -E 's/^.*[Ss]([0-9][0-9]).?[Ee]([0-9][0-9]).*/S\1E\2/p')
```

(I hope I managed to edit your line correctly)

even better making use of case insensitive matching
```
foo=$(echo $oldfilename|sed -n -E 's/^.*s([0-9][0-9]).?e([0-9][0-9]).*/S\1E\2/ip')
```

Martin

---

### Post by TaiChiRabbit on 2016-02-13
Martin
Thank you for both tips!  Works a treat with the extended option.

---

