---
title: "phpbb language package in ubuntu"
date: 2007-11-04
forum: General Help
---

### Post by bullgr on 2007-11-04
hi...
i installed yesterday in my ubuntu server the phpbb2 packaging including phpbb2-language pack from the ubuntu repos.
because i wanted to run the forum in my native language (greek) i notice that the translation is in greek iso 8859-7 text coding. the translation are done i believe from winblows users.
but i use ubuntu and in ubuntu the text coding (to write greek) is utf-8... so, when i try to setup my forum (categories, topics etc) i get the known wierd text garbage.
if i turn to iso 8859-7 coding in my web browser i get the traslated greek text fine, but mine greek writings are shown as garbage, and vince versa when i turn utf-8 to text coding.

finally, i convert all the greek language files to utf-8 with the iconv command.
example:
iconv -f iso-8859-7 -t utf8 iso_file.txt > utf_file.txt
and now i use utf-8 in my forum and i can read and write correctly in greek. tested also in winblows with ie, opera, firefox and works great too.

note that in english were is not any problem. no matter you change any text coding you like, you get correctly english...

we are not winblows users, and it's wrong to have language files in 8859-XX. why are then we using utf-8 in ubuntu?
these language files are ok for winblows users, but in want to setup a greek forum in ubuntu server and these files with this text coding is useless.

so, my question is, what need to do, to change the package developers the iso 8859-7 greek translating files from phpbb2-language pack with my ones in utf-8? with who i must contact? 
it's not a bug and it's specific for ubuntu/debian users. winblows users have not problem with iso 8859-7 text coding and it's useless to contact with the phpbb developers-forum.

thanks...

P.S.
it's good to done this with the other languages too. it's about 52 languages in the package.
maybe someone can make a script using the iconv command to convert all 52 languages.
i am not experienced with script writing. :-s

---

### Post by bullgr on 2007-11-04
bump... these category goes fast!!!

---

