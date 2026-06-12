---
title: "Recursively add leading dot"
date: 2015-08-19
forum: General Help
---

### Post by jdusablon on 2015-08-19
Hi everyone, I haven’t posted in many years.

I'm actually embarrassed I can't figure this out myself and my searches have been bizarrely fruitless...

How can I recursively rename files containing a certain pattern (like ending in .jpg) so that the filename contains a leading dot, making it hidden?

I've tried various iterations of for in;do loops with mv and rename as well as find -exec one-liners. I can successfully rename *.jpg files with a leading dot within a single directory, but I'm perplexed that I haven't managed to perform this recursively...

Thanks for your help in advance!

---

### Post by tgalati4 on 2015-08-19
Post what you have and we can tinker with it.  

If you are only going to perform this operation once per year then I would use the *find* command and dump results to a file.  Then use your rename script to operate on entries in the file.  It will be a flat file with a list of complete-path file entries that match your criteria.  However, if some files get tagged that you don't want to rename, you need a way to review the candidate list before actually renaming the files.  It would not be good practice to hide files in an automated fashion--that could cause problems if you make a mistake in your selection criteria.

You could put all of this in a script:  (pseudo code)

1.  Ask for selection criteria and store in a variable. 
2.  Ask for the top-level directory from which to start the downward search.
3.  Use *find* command create a flat list of files that match this criteria. Automatically recurses from the top level directory specified in 2.
4.  *more* the selection candidates so you can quickly review the list to make sure you don't tag any files that you don't want to change.
5.  Accept or Cancel, if Cancel launch a text editor so you can remove items that you don't want in the list.
6.  If Accept run through your name-change script which prepends a "dot" in front of each filename--include output to standard out so you can see each file as it gets changed.  Also write to a log file so you have a record of date and time when files were changed.
7.  Done.

This gives you a semi-automatic script which would be safer than a completely automatic script for this workflow.

---

### Post by Lars Noodén on 2015-08-19
rename uses perl expressions, so anything you can do in perl you can do in rename.  You could try something like this:

```

find . -type f -name '*.jpeg' -exec rename -vn 's#[color=blue]([^/]*)$[/color]#[color=green].$1[/color]#' "{}" \;

```

If you  provide some examples we could be sure, but that is just a guess.  

Normally s/// uses slashes as a delimiter but since we're looking (or not looking) for a slash, we'll use hashes # as the delimiter.  s###
In the search, we'll look for the largest block of characters through to the end of the line, that does not include a slash, and save it.
In the replace, we'll print a dot followed by what we found.

---

### Post by jdusablon on 2015-08-19
Thanks for the responses!

Here is my scenario: Have a WDTV, reads from a samba share. I use a script (sheetmaker) to generate nice thumbnails. In my first pass of my media, I forgot to include the leading dot to hide them from the WDTV, so I have several hundred folder.jpg and thumbnails (name.of.episode.jpg) files. I would like to rename these .folder.jpg and .name.of.episode.jpg to make them hidden.

P.S. Lars, thanks, I will try that... I'm not well versed in the rename variable syntax, it doesn't seem to work like sed.
P.P.S. I am soon buying a Raspberry Pi on which to install openelec, but it's just bugging me that I can't do this.

---

### Post by Lars Noodén on 2015-08-19
The formula above only does the files not the directories, but it is easy to modify find.

About the perl, rename uses full out perl, which some might describe as awk on steroids.  The [perl expressions](http://manpages.ubuntu.com/manpages/trusty/en/man1/perlre.1.html) give really powerful capabilities.  They're very worth learning because they are so useful and they also show up in many other places under the name PCRE.

---

### Post by HermanAB on 2015-08-19
Hmm... beware of things like *. or .*, because * includes . with the result that you can get .. which is the previous directory and then it recursively goes off and destroys the whole disk...

---

