---
title: "[SOLVED] How do I search for a string in a zip files"
date: 2015-05-22
forum: General Help
---

### Post by Robbyx on 2015-05-22
I used foremost to produce a long list of very varied content zip files. I am looking for the one file that has a file in it that contains a specific string. There is no need to search those zip files that have files named chrome in them. How is such a search done?

I tried kfind, but can it do what I want?

---

### Post by Lars Noodén on 2015-05-22
You could use zgrep though it is a little slow.  It takes almost the same options and arguments as grep.

---

### Post by Robbyx on 2015-05-22
> **Lars Noodén said:**
> You could use zgrep though it is a little slow.  It takes almost the same options and arguments as grep.

What is the syntax for the following?

zgrep [search for string]] 12456 [in all the zip files in the directory,  but only search in  xml files ]

---

### Post by Lars Noodén on 2015-05-22
It can only be pointed at filenames identified by [globbing](http://manpages.ubuntu.com/manpages/utopic/en/man7/glob.7.html). So you could look at all files ending in .xml.zip like this:

```

zgrep 123456 ./*.xml.zip

```

That looks for the string 123456 in those files.

---

### Post by Robbyx on 2015-05-22
I tried this but as you can see it did not work:

obins@robins-EP35-DS3L:/media/xhd_system_data/recover_Fri_May_22_10_12_37_2015/zip$ zgrep -Ir --include=*.xml CMP009753
/bin/zgrep: -r: option not supported
robins@robins-EP35-DS3L:/media/xhd_system_data/recover_Fri_May_22_10_12_37_2015/zip$ zgrep -I --include=*.xml CMP009753
/bin/zgrep: --include=*.xml: option not supported
robins@robins-EP35-DS3L:/media/xhd_system_data/recover_Fri_May_22_10_12_37_2015/zip$ zgrep -Ir --include=*.xml CMP009753

---

### Post by Robbyx on 2015-05-22
You could you please tweak your suggestion because this is what I get:

robins@robins-EP35-DS3L:/media/xhd_system_data/recover_Fri_May_22_10_12_37_2015/zip$ zgrep CMP009753 ./*.xml.zip
gzip: ./*.xml.zip.gz: No such file or directory

---

### Post by Lars Noodén on 2015-05-22
If you want to look in gzipped or zipped files that have names ending in .xml for the string CMP009753 then you could use this:

```

zgrep -l CMP009753 *.xml

```

The -l option tells it to display only the file name(s) and not the lines that are found.

---

### Post by Robbyx on 2015-05-22
It doesn't seem to work!

robins@robins-EP35-DS3L:/media/xhd_system_data/recover_Fri_May_22_10_12_37_2015/zip$ zgrep -l CMP009753 *.xml
gzip: *.xml.gz: No such file or directory

---

### Post by Lars Noodén on 2015-05-22
I only get an error like that if there are no files matching that pattern in that directory.  What is the output of 'ls' ?  Are you in the right directory or looking for the right filename?

---

### Post by HermanAB on 2015-05-22
If you want to recurse directories, use find with the exec option.

---

### Post by btindie on 2015-05-22
You could also try something like the following which will tell you the name of the zip file it finds the string in
```
for zip in *.zip; do unzip -p $zip \*.xml 2>/dev/null | grep -q 'CMP009753' && echo "Found in $zip"; done
```
You can then just unzip the file it finds to a new directory and use grep to find the xml file the string is in.

---

### Post by Robbyx on 2015-05-22
> **Lars Noodén said:**
> I only get an error like that if there are no files matching that pattern in that directory.  What is the output of 'ls' ?  Are you in the right directory or looking for the right filename?

ls produces a large number of zip files, xml files are stored in the zip files..

---

### Post by Lars Noodén on 2015-05-22
If the files end in .zip then you have to tell zgrep to look at them and not others.  

```

zgrep -l CMP009753 *.xml.zip
# or
zgrep -l CMP009753 *.zip

```

Feed zgrep the same file name pattern you would feed to ls.

---

### Post by Robbyx on 2015-05-22
> zgrep -l CMP009753 *.xml.zip
# or
zgrep -l CMP009753 *.zip

I am sorry for not making my problem clear to you, because the solution you suggest as quoted above does not work in my situation of having multiple files inside many different zip files and my only wishing to search the xml ones. The very good news is that btindie's proposal has worked and I have had remarkable results from all your help. I was not only able to find the files containing the string but was able to read them fully formatted in libreoffice writer by simply changing the zip extension to odt!

I am really surprised that I was able to get this far with finding the contents of a crashed  file and thank you all for your help

---

### Post by Lars Noodén on 2015-05-23
I'm glad it's fixed.  ODF it pretty easy to work with.  I see now that there were multiple files inside each zip file. That's where I was off, I thought it was a 1:1 match.

---

