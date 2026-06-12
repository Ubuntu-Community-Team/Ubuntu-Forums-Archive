---
title: "Sed (?) - replacing a set of characters in a file"
date: 2006-10-13
forum: General Help
---

### Post by Kure on 2006-10-13
Hello,

I would like to ask any "sed experts" to help me solve my problem. I have a huge backup of database (26 MB) and I need to remove certain lines, having this pattern:
```

INSERT INTO phpbb_search_wordlist (word_text, word_id, word_common) VALUES('**???**', '**???**', '**???**');
```

Here is an example:
```
INSERT INTO phpbb_search_wordlist (word_text, word_id, word_common) VALUES('napit, '22050', '0');
INSERT INTO phpbb_search_wordlist (word_text, word_id, word_common) VALUES('nepeveden, '161497', '0');
INSERT INTO phpbb_search_wordlist (word_text, word_id, word_common) VALUES('mta', '21', '0');
INSERT INTO phpbb_search_wordlist (word_text, word_id, word_common) VALUES('me', '20', '0');
INSERT INTO phpbb_search_wordlist (word_text, word_id, word_common) VALUES('mohlo', '19', '0');
INSERT INTO phpbb_search_wordlist (word_text, word_id, word_common) VALUES('linky', '18', '0');
```

I have to remove hundreds of thousands of lines - and I can't force sed to do such task.

My second question - is there a gui for a similar tool like sed? You know, most commands are readable and understandable, but expressions like this ```
sed -e '/^ *$/d' phpbb_db_backup.sql
``` are just too much for me.

Thank you for any answer.

---

### Post by PriceChild on 2006-10-13
*moved to general help*

---

### Post by der_joachim on 2006-10-14
You probably want to use tr, which is short for 'translate'. You should check the man page on tr, but you probably need the -d option, which stands for delete.

As for graphical tools, any good text editor with a decent search and replace function should do, although I do not know assume that your DB backup is a text file.

---

### Post by MacMan on 2006-10-14
> **Kure said:**
> Hello,

I would like to ask any "sed experts" to help me solve my problem. I have a huge backup of database (26 MB) and I need to remove certain lines

I hope I've understood your problem correctly. Try this:
```
grep -v "INSERT INTO phpbb_search_wordlist (word_text, word_id, word_common) VALUES(.*,.*,.*);" your_file > new_file
```

It's not sed but I tried it on your example lines and it worked.

> My second question - is there a gui for a similar tool like sed? 

There is a "graphical regular expression editor" for KDE called kregexpeditor. It may help you building regular expressions for sed.

I hope this helps.

Ciao.

---

### Post by Kure on 2006-10-14
Thank you for your suggestions - I've solved the problem by manually editing the file (fortunately in plain text) in Scite, the only editor which was able to open it effectively - I guess vim could do the job too, but in a more complicated way.

---

