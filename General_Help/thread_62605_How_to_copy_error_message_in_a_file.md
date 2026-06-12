---
title: "How to copy error message in a file?"
date: 2005-09-05
forum: General Help
---

### Post by Tubuntu on 2005-09-05
How I can copy error message in a file?  (using "command line")  


Thanks

---

### Post by nozey on 2005-09-05
I didint understood your question ... 

But u can copy stuff from terminal using the mouse.
You select what uou want to copy, and to paste u use the mouse middle button(or left and right buttons togheter).

You can use "> to send the errors messages to a file. 
Exemple:

```
$ sudo /etc/init.d/apache2 > erro.txt
```

The message that should appear on screen , will be sent to the file: "erro.txt" .
And you can see it using:

```
$ cat erro.txt
```

---

### Post by Tubuntu on 2005-09-05
"You can use > to send the errors messages to a file" 
That I was looking

Thank you nozey

---

