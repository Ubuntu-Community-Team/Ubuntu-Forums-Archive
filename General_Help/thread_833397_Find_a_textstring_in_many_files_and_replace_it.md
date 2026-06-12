---
title: "Find a textstring in many files and replace it"
date: 2008-06-18
forum: General Help
---

### Post by xodeus on 2008-06-18
Hi there. I have a huge collection of files, which I would like to edit. I know that it's possible, but don't know how.
The files are in /home/mariusz/work/themes and in multiple directories there. Now i want to find a text string that looks like "xyz1224" and replace it with "1234xyz". How do I do that?

---

### Post by geirha on 2008-06-18
This one will search all files in that directory for the string 'xyz1224', and print these occurances.
```

find /home/mariusz/work/themes -type f -print0 | xargs -0 grep --color=auto 'xyz1224'

```
If all those occurances should be replaced, run this command:
```

find /home/mariusz/work/themes -type f -print0 | xargs -0 sed -i 's/xyz1224/1234xyz/g'

```
If not, ask more detailed. Give some example data that should be replaced, and some that shouldn't be replaced for example.

---

### Post by xodeus on 2008-06-18
This really worked. Thank you. Maybe will this one get more tricky one.
I've this textstring > Feel free to <a href="http://blogono.com/wp-create.php">create free blogs</a> with <a href="http://blogono.com">Blogono Free Blog Hosting</a>
And I want it to be replaced with
> <a href="http://bloggr.dk/wp-create.php">Opret</a> en gratis <a href="http://bloggr.dk">bloggr.dk</a> blog.
same files, same structure. Is this possible the same way?

---

### Post by geirha on 2008-06-18
The url part is straight forward, you change "http://blogono.com" to "http://bloggr.dk". Just a slight problem though, since the sed uses the '/' character as a special delimiting character and '.' is a "match all"-character, but sed can use a different one (the first character after the s will be used) and the dot can be escaped to match only '.'.

The grep and sed parts of the previous commands would become
```

 ... grep --color=auto 'http://blogono\.com'
 ... sed -i 's|http://blogono\.com|http://bloggr.dk|g'

```
For the other parts, I think manual translation is in order, because the translated words change positions relative to the other words, and it will just get incredibly complex.

---

### Post by xodeus on 2008-06-18
You are the guru. The url was even easier as it only was the blogono.com which changed to bloggr.dk and it was easy. Thank you so much...

---

