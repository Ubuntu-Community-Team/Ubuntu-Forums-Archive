---
title: "List all custom files in /etc and /usr?"
date: 2017-03-09
forum: General Help
---

### Post by &amp;KyT$0P# on 2017-03-09
I have many files scattered throughout [FONT=Courier New]/etc[/FONT] and [FONT=Courier New]/usr[/FONT] which are either A) not part of any installed package, or B) have been modified after installing the package.

How to get a list of all these files?

---

### Post by vasa1 on 2017-03-09
Re. */etc*, TheFu posted this: [https://ubuntuforums.org/showthread.php?t=2303338&p=13392820#post13392820](https://ubuntuforums.org/showthread.php?t=2303338&p=13392820#post13392820)

I know it's not exactly what you asked for.

---

### Post by &amp;KyT$0P# on 2017-03-10
Thanks vasa1.  I do have some full-system backups.  But they are all too recent and too infrequent to be of use for this.

---

### Post by Keith_Helms on 2017-03-10
If I was going to do this, I'd probably write some scripts that

a) Build a master list of all files in /etc and /usr
b) Go through the list of all installed packages on my system
c) Download the package files for each into some directory with [I]apt-get download packagename
[/I]d) Unpack the deb files into a work directory with *dpkg --unpack debfile*
e) Diff the unpacked files with those in /usr and /etc and remove matches from the master list.
f) What's left would be files that didn't originate from a deb file or have been modified since install.

Sounds like a lot of work, but it should do what you describe.

Or, you could just make a practice of putting a comment in any config file you change or create and just search for them using grep. :)

---

### Post by &amp;KyT$0P# on 2017-03-10
Thanks Keith_Helms, I'll do something along those lines.  Downloading literally every package I have installed would probably be too much for my Internet connection.  But in the mean time, I found [this]("http://www.tecmint.com/check-verify-md5sum-packages-files-in-linux/"), which hopefully will reduce the number of packages I need to download/diff.

---

### Post by &amp;KyT$0P# on 2017-03-10
I installed [FONT=Courier New]debsums[/FONT], and got a list of files with MD5 checksum mismatch.  And I'm currently using [FONT=Courier New]find[/FONT] and a shell script to scan [FONT=Courier New]/etc[/FONT] and [FONT=Courier New]/usr[/FONT] for files that don't belong to any package.
```
#!/bin/ksh

dpkg-query -S "$1"
[ x"$?" = x'1' ] && echo "$1" >> "$2"

```

But that still doesn't cover everything, does it?  I still have to use Keith_Helms' method to check the installed packages which don't have md5sums.

How to list all such packages?

---

### Post by &amp;KyT$0P# on 2017-03-11
> **halogen2 said:**
> And I'm currently using [FONT=Courier New]find[/FONT] and a shell script to scan [FONT=Courier New]/etc[/FONT] and [FONT=Courier New]/usr[/FONT] for files that don't belong to any package.
Apparently that is horribly inefficient in [FONT=Courier New]/usr[/FONT] and brings many irrelevant results, including all the auto-generated .pyc files.  Not helpful.

For list all the files that are not part of any installed package.  Would it work to make a shell script that does this? -

1) Get a list of all package-installed files
```
dpkg-query -L $(aptitude --disable-columns -F '%p' search '?installed')
```
Run that through [FONT=Courier New]sort[/FONT], and then [FONT=Courier New]uniq[/FONT].  Dump the result in 'dpkg_installed_files'.

2) List all possibly-relevant files in [FONT=Courier New]/etc[/FONT] and [FONT=Courier New]/usr[/FONT]
```
sudo find -P /etc /usr -type f ! -iname \*.pyc
```
Run that through [FONT=Courier New]sort[/FONT], and then [FONT=Courier New]uniq[/FONT].  Dump the result in 'found_files'.

3) Do a diff and filter the output -
```
diff dpkg_installed_files found_files | grep -P -i '^>'
```

---

### Post by &amp;KyT$0P# on 2017-03-11
This was getting near the bottom of page 2, so, bump.  Sorry if it's too soon.

---

### Post by Keith_Helms on 2017-03-11
You may be on your own here.  It doesn't sound like something that would be very commonly attempted.  I wasn't aware the lists of md5sums existed and, if they don't exist for all packages, I'd guess you'd have to supplement that approach with having to extract files from packages and diff them to the filesystem version.

I'm not at home this month where I would have fast and unmetered internet to allow me to play with this.

---

### Post by &amp;KyT$0P# on 2017-03-13
Re: packages without md5sums, I discovered this was installed along with debsums -
```
$ cat $(which debsums_init)
#!/bin/sh -e
# Copyright (C) 2007 Osamu Aoki <osamu@debian.org>, Public Domain
# Find out missing *.md5sum and add it to the list
cd /var/lib/dpkg/info
for package in $(debsums --list-missing); do
  echo "checking $package"
  if [ ! -e $package.md5sums ]; then
    echo "******* $package.md5sums missing *******"
    apt-get --download-only --reinstall --yes install $package || true
    debsums --generate=nocheck -p /var/cache/apt/archives $package || true
  fi
done
echo "Finished generating md5sums!"
echo "Checking still missing md5files..."
debsums --list-missing

```
[FONT=Courier New]debsums --list-missing[/FONT] doesn't print anything for me.  Does this mean all the installed packages actually **do** have md5sums?

---

### Post by Keith_Helms on 2017-03-13
Have you strung all the pieces together so that you're getting a list of files that were changed or added?

---

### Post by &amp;KyT$0P# on 2017-03-13
Not yet.  This got the changed and removed files, at least for packages with md5sums -
```
sudo debsums -ac
```

Still working on a shell script for added files.

---

### Post by &amp;KyT$0P# on 2017-03-14
> **halogen2 said:**
> [FONT=Courier New]debsums --list-missing[/FONT] doesn't print anything for me.  Does this mean all the installed packages actually **do** have md5sums?
Well, I asked this because the man page for debsums is worded somewhat vaguely -
```
       -l, --list-missing
              List packages (or debs) which don't have an MD5 sums file.

```

But apparently it's a silly question.  [FONT=Courier New]debsums --list-missing[/FONT] isn't listing .deb files with missing md5sums, it lists which installed packages don't have md5sums.  So [FONT=Courier New]debsums --list-missing[/FONT] is how to get a list of the packages that would require [this treatment]("https://ubuntuforums.org/showthread.php?t=2355158&p=13618626&viewfull=1#post13618626").


I will mark this solved when I have a working script to list files not belonging to any installed package.

---

### Post by HermanAB on 2017-03-14
Interesting problem...  I would make a virtual machine of the original installed version and then use a backup utility like rsync to do a dry run copy from the one to the other, to get a list of changes without actually doing any copying.

$ man rsync
-n, --dry-run               perform a trial run with no changes made

---

### Post by &amp;KyT$0P# on 2017-03-28
I put it all together in a shell script which boils down to this -

1) Check for changed md5sums
```
sudo debsums -ac 2>&1
```

2) Discover all files installed by packages
```
echo 'Reading installed file lists' >&2
PKG_FILES_RAW=$(mktemp)
dpkg-query -L $(aptitude --disable-columns -F '%p' search '?installed') > "$PKG_FILES_RAW"

echo 'Sorting...' >&2
sed -r -e 's/^(package\s+diverts\s+others|diverted\s+by\s+\S+)\s+to:\s+//g' -i "$PKG_FILES_RAW"
sort "$PKG_FILES_RAW" | uniq
```

3) Find certain files in /etc and /usr
```
sudo find -P /etc $(ls -A /usr | sed -r -e '/^local$/d' | sed -r -e 's#^#/usr/#g') -type f ! -iname \*.pyc
```
Pass the result to [FONT=Courier New]sort | uniq[/FONT]

4) Run diff of the list from (2) and the list from (3).  Pipe the result to [FONT=Courier New]grep -P -i '^>'[/FONT]

5) If something needs to be done manually, print out the download command -
```
echo apt-get download $(debsums --list-missing) >&2
```

Thanks all! :KS

---

