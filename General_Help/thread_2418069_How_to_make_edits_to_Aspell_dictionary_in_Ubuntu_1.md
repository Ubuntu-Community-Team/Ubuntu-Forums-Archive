---
title: "How to make edits to Aspell dictionary in Ubuntu 18.04"
date: 2019-05-01
forum: General Help
---

### Post by swarup on 2019-05-01
I have installed Ubuntu 18.04; although Aspell is installed and I have installed the Hindi dictionary, but I need to install my personal word list into the dictionary. I have my custom file hi.cwl, but I am not certain where to install it.

I wanted to try to figure things out myself as far as possible, and I found what I thought might be the correct location: /usr/share/aspell/hi.cwl.gz

So I tried removing the file hi.cwl.gz from there, and replacing it with my hi.cwl.gz. I have rebooted the computer, started the spellchecker in Gedit, and opened a Hindi file and spellchecked it. I have also converted an instance of my custom hi.cwl to its hi.wl form, opened it in Gedit, and compared the words to those underlined in red in my test hindi document. There are lots of words in the hi.wl file which are underlined in red in the test document, proving that the hi.cwl.gz file which I have installed is not working in the spellchecker. I do not know what hi.cwl the Aspell program is using, but it is not using the hi.cwl.gz file which I installed.

I will also add that in my home folder, there is a folder /home/swarup/.config/enchant, and in this enchant folder there are number of dictionary files including these two:

/home/swarup/.config/enchant/en_US.dic
/home/swarup/.config/enchant/hi.dic

I know for a fact that the Gedit spellchecker uses these, as they correspond with the words underlined and not underlined in my test document when I select spell checker language as English or as Hindi. And it was like this in my Ubuntu 14.04 LTS installation as well. But it used to use my hi.cwl file as well. I used to regularly open the hi.cwl file as an hi.wl and add words to it, and it worked fine. And when I would be working in a Gedit file and come across a single red underlined word and click on the spellchecker option to add it to the dictionary, then it would add it to /home/swarup/.config/enchant/hi.dic. In that way, I have 11,000 words in this file. But I also have 90,000 words in my hi.cwl file, and so the functionality of this file is also vital to the spell checker.

Kindly let me know how to move ahead so as to get the hi.cwl file working. Do you think it may need to do cd to the folder and execute the commands ./configure, make, sudo make install? That is what I always used to have to do to get updated instances of my hi.cwl file active in Aspell in Ubuntu 14.04 as well as previous installations of Ubuntu. In those days though it was hi.cwl which was installed and not hi.cwl.gz; don't know what impact this has on what is needed to activate the hi.cwl file.

---

### Post by swarup on 2019-05-06
There must be someone who updates their Aspell dictionary....it is a routine task, just don't know how to manage it in 18.04....

---

