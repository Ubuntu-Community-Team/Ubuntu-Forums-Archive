---
title: "Rename all files in drive"
date: 2016-09-20
forum: General Help
---

### Post by sed_faster on 2016-09-20
HEllo everyone,

I have a many files, more a less, one million files (e.g. pdf, html, php, etc), and I need tag all of them which a different code. I thought of create a script which runs through tree of directory and add, in name file, a tag for example "tag_001".
I have a little knowledge about shell script and I think I will need this:


[LIST]
[*]    report all my files, maybe use programm tree;
[*]    create a loop while, which will be run as many times of value acquired in report, respective of number files catch;
[*]    execute, into loop while, the command "mv file_old file_tag_00i" -> where variable "i" is a number of the cycle respective of loop;
[/LIST]

I am in good path or you guys have a better idea?
Sorry about my english, if do you need I can explain again, thanks

---

### Post by &amp;KyT$0P# on 2016-09-20
> **Edgar_Oliveira said:**
> [LIST]
[*]    report all my files, maybe use programm tree;
[*]    create a loop while, which will be run as many times of value acquired in report, respective of number files catch;
[*]    execute, into loop while, the command "mv file_old file_tag_00i" -> where variable "i" is a number of the cycle respective of loop;
[/LIST]

Here is what I would try -
[LIST]
[*]Use the [FONT=Courier New]find[/FONT] command to get the list of files;
[*]use a [FONT=Courier New]for[/FONT] loop to iterate through them;
[*]execute inside the for loop, the mv command you wrote, and also increment a number.  Here's an example of how the counting would work -
```
i=0
for s in abc def ghi;do
  echo "$s $i"
  i=$(($i + 1))
done
```
[/LIST]

---

### Post by sed_faster on 2016-10-18
Hello,

Thanks for the advice. I upload this script in my github, please feeling free to increase or opinion about this script: [https://github.com/EdgarOliveira/scriptlinux/blob/master/exsh36.sh](https://github.com/EdgarOliveira/scriptlinux/blob/master/exsh36.sh)

---

