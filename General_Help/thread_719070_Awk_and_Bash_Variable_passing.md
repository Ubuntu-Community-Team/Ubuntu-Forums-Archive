---
title: "Awk and Bash Variable passing"
date: 2008-03-08
forum: General Help
---

### Post by Mr.Macdonald on 2008-03-08
I am writing a CGI script in Bash and Awk

I need to pass Two variables into an awk statement
heres my code

ls -1 ./"$CMD" | awk -F'\n' '{ for (n=1;n<=NF;n++) { print "<a href=\"./" **$CMD** "/" $n "\">" $n "</n><br>" } }'

the CMD is a directory
n loops through the files in that directory by line breaks
the bold is junk code that is wrong

i need to print a link to all the files inside said directory
CMD is dynamic in that its changed by the user so plain text won't work
printing the path into the awk won't work because it risks security because the user could see my directory structure

Sorry code is messy

Suggestions can come in all forms in that I could make a Java OR C++ program to solve this but would prefer not to

I only know C/C++, Java, Bash, Awk, Visual Basic(Laugh, i was forced to in school please don't hate my for touching the devils work)

---

### Post by ghostdog74 on 2008-03-08
to pass variable from shell to awk
```

awk -v cmd="$CMD" '{ ..... cmd .....}' 

```

---

### Post by Mr.Macdonald on 2008-03-09
It didn't seem to work

$ CMD="hello"
$ echo good bye | awk -v cmd="$CMD" '{ print $1 $cmd $2 }'
goodgood byebye


I expected

goodhellobye


Never mind i needed to do

echo good bye | awk -v cmd="$CMD" '{ print $1 cmd $2 }'


Sorry

---

