---
title: "What does &gt; mean?"
date: 2018-01-21
forum: General Help
---

### Post by andysharpie on 2018-01-21
I get this prompt every time I try to change to a sub directory and don't know what to do with it.

Andy

---

### Post by QIII on 2018-01-21
Hello!

Would you please post both the command you are issuing and the complete message?

Thanks!

---

### Post by sisco311 on 2018-01-21
> is the default value of PS2, the secondary prompt string. The secondary prompt is displayed when the shell needs more input to complete a command. 

```
[sisco@asrock ~]$ PS2="Please continue > "
[sisco@asrock ~]$ echo "line1
Please continue > line2
Please continue > line3
Please continue > end"
line1
line2
line3
end


```

For more info check out the manual:
```

man bash | less "+/^ +PS2"
man bash | less +/^PROMPTING
```

---

### Post by Impavidus on 2018-01-21
Does the directory you want to change to by any chance contain an apostrophy or double quote ( ' " )? They're created by default with some language settings. For example, with dutch setting you get the Video's directory. If I want to change to that and type```
cd Video's
```followed by enter, the shell shows > on the next line because it assumes that I want to include the newline character (but not the apostrophy) in my command and allows we to continue typing. After all, I quoted the newline. The way to solve that is to escape or quote the quote:```
cd Video\'s
cd "Video's"
```

---

### Post by andysharpie on 2018-01-21
Thank you to Impavidus for clearing that up. Yes, I was trying to go to a directory with an apostrophe.

Andy

---

### Post by sisco311 on 2018-01-21
Tab completion! ;)

---

