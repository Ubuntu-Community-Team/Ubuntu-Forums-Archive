---
title: "shell - print a file from a given position"
date: 2007-10-01
forum: General Help
---

### Post by Tex-Twil on 2007-10-01
Hello,
I have a text file with words in it. Each line contains one word. I would like to print (cat) the file from the line containing a given word till the end but I'm a bit stuck.

What are the commands I should pipe together to obtain this ?

Thanks,
Tex

---

### Post by mali2297 on 2007-10-01
> **Tex-Twil said:**
> Hello,
I have a text file with words in it. Each line contains one word. I would like to print (cat) the file from the line containing a given word till the end but I'm a bit stuck.

What are the commands I should pipe together to obtain this ?

Thanks,
Tex

This is easily done with *grep*:
```

grep word filename

```

---

### Post by Tex-Twil on 2007-10-01
Hi,
I think I wasn't clear enough. The command you wrote will just output the gived word if it's contained in the file.

What I want is to output **all the words after** the given one. For example in a file containing 
> 
sunday
monday
tuesday
[B]wensday
thursday
friday
saturday[/B]


I'd like to print the bold words if I specify "wensday".

Thanks

---

### Post by mali2297 on 2007-10-01
Alright, sorry. 

Try
```

grep -A number word filename

```
where *number* is the number of lines that should be printed. (Make it a large number and it will print all the lines after the word.)

---

### Post by Tex-Twil on 2007-10-01
Ok that looks good, thanks

---

