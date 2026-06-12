---
title: "Help with grep syntax"
date: 2016-01-18
forum: General Help
---

### Post by greyghost60 on 2016-01-18
Hi
I have a problem try to locate a file. I know it contains a phrase but the file could be a document or a spreadsheet or a presentation. To complicate things further it could be in any folder under the home directory

I know grep should do it but I can't find the right syntax it seems to want a file patten which I don't have. Any ideas would appreciated

Regards

Greyghost60

---

### Post by btindie on 2016-01-18
Firstly, Linux doesn't differentiate between "a document or a spreadsheet or a presentation", they're all just files with different names.

Grep is probably the wrong command as that searches through files for a match.

If you what to find a file with a particular name then use the 'find' command. e.g.
```
$ find ~/ -type f -iregex '.*/my document.*'
```
That searches for a File using a case-insensitive regular expression. The find command defaults to Emacs Regular Expressions but that can be changed.

See 'man find' for more info.

---

### Post by greyghost60 on 2016-01-18
hi Thanks for the quick reply 

What I am looking for is the name of the file which contains the phrase in any folder or sub-folder under home.

something like 

Select filename where file contains " a nice day"

---

### Post by steeldriver on 2016-01-18
I don't think you're going to be able to use raw grep for that - some of the file types you mentioned (document / spreadsheet / presentation) are likely to be in a binary or compressed format that's not directly searchable using simple text-based tools

For .odt (and iirc .docx) you can unzip the "file" and search the underlying XML content, but I'm not sure that the same trick will work for your other target file types

---

### Post by btindie on 2016-01-18
If it's the contents you're wanting to search than that will be more tricky as they're likely to be binary files and not contain plain text.

You could try
```
$ grep -ir 'a nice day' *
```

which will search every file in every directory in your home directory so could take a while...

If you keep your documents in ~/Documents you'd be better off running it from there.

Caution: if you've got any movies or iso files it'd also search them.

You may want to create a list of files based on file extension and run grep on them, e.g.
```
$ find ~/ -type f \( -name '*.doc' -or -name '*.docx' \) -print0 | xargs -r -L1 -0 grep -H 'a nice day'
```
But as they're binary files it probably won't find what you're after.

---

### Post by vasa1 on 2016-01-18
I Googled for "grep ods files" and one hit was this: [http://www.techrepublic.com/blog/linux-and-open-source/how-to-search-for-text-inside-many-opendocument-files/](http://www.techrepublic.com/blog/linux-and-open-source/how-to-search-for-text-inside-many-opendocument-files/)

It linked to this UF thread: [[SOLVED] Search multiple .odt files]("http://ubuntuforums.org/showthread.php?t=899179").

The code posted in post [#6]("http://ubuntuforums.org/showthread.php?t=899179&p=5653470#post5653470") in that thread, modified just a bit:

```
for i in *.od*;
do unzip -ca $i | grep -q "vasa1";
    if [ $? -eq 0 ];
        then echo "string found in $i";
    fi;
done
```gave me this output:```
string found in Budget.odt
string found in new-member-history.ods
unzip:  cannot find or open notice, notice.zip or notice.ZIP.
string found in SocContacts.ods

```There maybe a way to run that code recursively but I'm not good at this stuff.

---

### Post by steeldriver on 2016-01-18
You could try something like

```

find path/to/dir \( -name "*.odt" -o -name "*.ods" \) -exec sh -c 'unzip -c "$1" content.xml | grep -Ho --label="$1" "search pattern"' sh {} \;

```

See this previous thread as well --> [http://ubuntuforums.org/showthread.php?t=2007652](http://ubuntuforums.org/showthread.php?t=2007652)

---

### Post by ajgreeny on 2016-01-18
If you fancy a GUI app to do this type of search have a look at **recoll** which is in the repos and I use occasionally.  There are a few file-types that it can't look in, but it has worked well for my needs.

---

