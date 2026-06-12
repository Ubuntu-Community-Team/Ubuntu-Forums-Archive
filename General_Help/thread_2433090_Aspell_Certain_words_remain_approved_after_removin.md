---
title: "Aspell: Certain words remain approved after removing from global &amp; custom wordlists"
date: 2019-12-13
forum: General Help
---

### Post by swarup on 2019-12-13
I have been using the Aspell spellchecker for years, and it works great. I use it for both English and Hindi.

Just one thing I need to solve: There are a number of words which I have removed from both the global Hindi word list as well as my custom Hindi word list. However, despite removing them from those two lists, the words continue to be accepted i.e. they are not underlined in red as they should be when I run the spellchecker.

The two locations from where I have removed the words are as follows. 

1. Global Hindi word list

Via command "aspell6-hi-0.02-0$ preunzip hi.cwl", the compressed file hi.cwl is unzipped to hi.wl in the folder /home/swarup/aspell6-hi-0.02-0/hi.wl

Then the hi.wl file can be opened, and the undesired words removed.

2. The custom Hindi dictionary world list 

/home/swarup/.config/enchant/hi.dic

3. Having removed the undesired words from these two lists, I again compress the file hi.wl to hi.cwl and do the following commands

./configure
make
sudo make install 

4. These words which have been removed from both the universal and custom dictionaries should then get underlined in red upon running the spellchecker. But they are not getting thus underlined. I believe that means there must be yet another word list somewhere which Aspell is using in addition to the above mentioned two lists. 

Aspell is functioning, and most of the words I remove from the above two lists then get underlined in red upon running the spellchecker. But there is a minority of words which do not get underlined even after removal from the above two lists. 

Please let me know what other files or folders I can search for perhaps a third Hindi word list where these unwanted words are getting stored and continue to be accepted by the spellchecker.

---

