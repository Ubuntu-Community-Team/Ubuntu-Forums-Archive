---
title: "How Do You Capitalise The First Letter Of Every Word In A Directory Va Terminal?"
date: 2017-11-07
forum: General Help
---

### Post by kamrynborden on 2017-11-07
Is there a command that I can use so I don't have to check each file manually? Thanks.

---

### Post by sudodus on 2017-11-07
What do you mean by every word?

- The first letter of every file name?

- The first letter of every word in every file name (if there are spaces in the file name)?

- The first letter of every word in every file (the content of text files) in the directory?

- And why do you want this?

---

### Post by kamrynborden on 2017-11-21
In a fire directory. so files like This Is a title.cph will be This Is A Title.cph for all files.

---

### Post by QIII on 2017-11-21
Hello!

Let me just poke my head in for a moment and suggest that file names with spaces are not a good idea.  They can cause no end of headaches and generally require an escape character to reference them in automation.

If you need a file that is human recognizable as "This is my file.file", it might be better to use "ThisIsMyFile.file" or "This_Is_My_File.file" -- or another format that does not contain spaces.

My two cents.  Play on.

Cheers!

---

### Post by vasa1 on 2017-11-21
And my contribution: [http://pclosmag.com/html/Issues/201607/page03.html](http://pclosmag.com/html/Issues/201607/page03.html)

---

### Post by Tadaen_Sylvermane on 2017-11-22
Agree with the no spaces thing. While I don't have to worry about automation my entire media library files are named with spaces. Easier to read, murder when I have to manipulate files for whatever reason. If I could do it over again I would but don't want to lose my database entries with current filenames.

---

### Post by untrustytahr on 2017-11-22
> **kamrynborden said:**
> Is there a command that I can use so I don't have to check each file manually? 

Yes, the command is "rename".   It uses regex (perlexpr).  If you're unsure of your expression use the -n to test the command before doing any renaming.

---

