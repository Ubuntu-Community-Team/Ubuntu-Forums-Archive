---
title: "Delete files based on file size"
date: 2016-08-24
forum: General Help
---

### Post by raleigh3 on 2016-08-24
I am interested in a script that would delete a file based on it's file size.

Ex.

Delete any .sh files equal 57 bytes.

This come close, it find files less than 57 bytes.

I need it to find files that are exactly 57 bytes.

 	 	 	 		 			 				```
sudo find . -name "*.sh" -size -57w 			 		
```

---

### Post by &amp;KyT$0P# on 2016-08-24
The man page for find doesn't seem to list a minus in front of the parameter given to -size, so what if you remove it?
```
sudo find . -name "*.sh" -size 57w
```

---

### Post by papibe on 2016-08-24
EDIT: yes c instead of b!

Hi raleigh3.

A couple of thoughts:

'w' stands for something different, you want to use 'c' for bytes.

You can actually use + and - to say 'less than' and greater than' (is in the man's section TESTS, which -size is part of).

So, to exactly match 57 bytes (similar to halogen2's):
```
find . -name "*.sh" -size 57**[COLOR="#FF0000"]c[/COLOR]**
```

That would just print the files you want to delete. This would also print their size (double checking your code):
```
find . -name "*.sh" -size 57c -ls
```

When you are 100% sure, those are the files you want to delete, run:
```
find . -name "*.sh" -size 57c -delete
```

Hope it helps. Let us know how it goes.
Regards.

---

### Post by raleigh3 on 2016-08-24
find . -name "*.sh" -size 57c worked.

```
'c'  

for bytes
```

---

