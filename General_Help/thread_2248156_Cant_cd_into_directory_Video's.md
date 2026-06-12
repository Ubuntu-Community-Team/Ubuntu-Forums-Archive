---
title: "Cant cd into directory Video's"
date: 2014-10-12
forum: General Help
---

### Post by zkr300 on 2014-10-12
When I type cd Video's or ls Video's

I get

>

as the prompt and nothing works furthermore, so I end the terminal or do CTRL c.

What is wrong?

I found it also strange, that ' before the s but I cant even change the name of directory Video's.

Please help.

Lubuntu 14.04

---

### Post by grahammechanical on 2014-10-12
If you run the command

```
ls
```

you will see that the directory/folder is Videos. Unless, you have renamed it or created another folder called Video's. It could be that the apostrophe ( ' ) is a special character the command line shell interprets as part of a command. And for that reason should not be used as a file or folder name.

Regards.

---

### Post by oldos2er on 2014-10-12
Apostrophes are interpreted in a way by the shell that causes the ">" to appear. Try ```
cd Videos
``` or ```
cd V[Tab]
``` and let the shell complete the folder name for you (minus any misspellings).

---

### Post by SeijiSensei on 2014-10-13
You should really avoid using special characters in file and directory names because they often have meaning in the shell. Along with the apostrophe ("single-quote") and the quotation mark ("double-quote"), characters like #, /, \, and $ are all meaningful.  If you have these characters in names, you need to "escape" them at the command line by preceding them with the backslash character \.  So you could have typed:
```
Video\'s
```
to tell the shell that the apostrophe should be treated literally.  But it's just easier to avoid them altogether.  

I also avoid embedded spaces as well since bash treats them as a delimiter.  If you have a name with embedded spaces, you need either to escape them, or put the name inside single quotes.  For instance, if you had a directory called "Pigs in Space", you'd need to refer to it as either
```
Pigs\ in\ Space
```
or
```
'Pigs in Space'
```
at the command line.  The latter example shows how the single quote works.  Wrapping a string in single quotes tells bash not to treat the spaces as delimiters, which is the way they are parsed normally.  The string
```
Pigs in Space
```
is treated as three separate entities when parsed by the shell.  The version inside single quotes is treated as a single entity.

To add even more complication, the single and double quotes [have different meanings]("http://www.howtogeek.com/howto/29980/whats-the-difference-between-single-and-double-quotes-in-the-bash-shell/"), too.

---

### Post by Impavidus on 2014-10-13
The default names for these directories (Pictures, Videos, Documents etc.) are localised and the dutch word for videos is video's, including the apostrophe. So this name with the apostrophe can be the default. It's indeed not very convenient as the shell thinks you are quoting something, like the newline character when you hit enter. You have to escape the apostrophe, like in```
cd Video\'s
```If you accidentally don't and hit enter, you can type another apostrophe and hit enter, as in```
$cd Video's
> '
bash: cd: Videos
: Bestand of map bestaat niet
```causing bash only to complain that the directory Videos<newline> doesn't exist. No reason to close the terminal.

---

### Post by jamesisin on 2014-10-13
Also, note that you can get out of > prompts by using ctrl-c.

---

### Post by SeijiSensei on 2014-10-13
> **zkr300 said:**
> When I type cd Video's or ls Video's

I get

>

as the prompt and nothing works furthermore, so I end the terminal or do CTRL c.

The ">" prompt means that the command is incomplete.  In this case it is waiting for you to enter another apostrophe to match in the one in Video's.

---

