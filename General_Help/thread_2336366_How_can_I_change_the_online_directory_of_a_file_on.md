---
title: "How can I change the online directory of a file on Google Drive with terminal"
date: 2016-09-07
forum: General Help
---

### Post by user3514 on 2016-09-07
Hi,

I am unable to use [gdrive]("https://github.com/prasmussen/gdrive") to change the online directory of a file that is already uploaded on Google Drive.

The only way that I have right now:


[LIST]
[*]Download the file
[*]update it with the desire location ( with "gdrive update ..." )
[/LIST]

I don't want to be forced to download the file all the time.

Thank you

---

### Post by oldos2er on 2016-09-07
Update it with the what?

I don't use gdrive, but if I understand correctly you wish to move a file to another folder on Google Drive? This is easily accomplished in a browser. If this is not the solution you want, I suggest you take it up with the developer, where I think you're more likely to get help.

---

### Post by user3514 on 2016-09-08
Thank you for your answer. I have a lot of files to sort and want to do it recursively for certain name patterns.

---

### Post by oldos2er on 2016-09-09
Ok, so the browser interface wouldn't be a good solution then. Thanks for clarifying.

---

### Post by user3514 on 2016-09-15
A function that download and upload the file at the right directory can be created.

For Google documents:

```
[COLOR=#000000]gdrive-change-dir-doc () {[/COLOR]

[COLOR=#000000]cd /root/.gdrive/files[/COLOR]
[COLOR=#000000]rm -i *[/COLOR]
[COLOR=#000000]gdrive export --mime application/vnd.openxmlformats-officedocument.wordprocessingml.document $1[/COLOR]
[COLOR=#000000]gdrive delete $1[/COLOR]
[COLOR=#000000]gdrive import -p $2 *[/COLOR]

[COLOR=#000000]}[/COLOR]

```[COLOR=#000000][FONT=Arial]
[/FONT]For non Google document files:
```

gdrive-change-dir-non-doc () {
    cd /root/.gdrive/files
    rm -i *
    gdrive download $1
    gdrive upload -p $2 *
    gdrive delete $1
}[FONT=Arial]
[/FONT]
```[FONT=Arial]

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]You can now create powerful command such as putting all unsorted docs in one online folder:

[/FONT][/COLOR]```
[root@computer][~]# drive list --absolute | grep -v "/" | grep doc| awk '{ print $1 }'|while read i
do
       gdrive-change-dir-doc $i <DESTINATION FOLDER>
done

```

---

