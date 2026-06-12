---
title: "Hebrew characters"
date: 2024-09-24
forum: General Help
---

### Post by etonry on 2024-09-24
A few years ago I was doing some computer work for an online friend.  He had a lot of stories in different languages and wanted a list of the titles.  Most were easy, but four were in Hebrew.  The text did not show Hebrew characters, just gibberish. The character set was wrong.  I spent a lot of time and finally figured out how to read the gibberish as Hebrew characters.  That let me put the titles into Google translate and learn what they were.

All fine.  Now this guy has passed the files to someone else, without the titles.  So I'm being asked to supply the titles again.  Unfortunately, I didn't make a note of the correct character set to decipher the gibberish.  I remember having a pull down list of character sets and going through them, one by one, until I found the right one.  I don't remember what program I used.  I think it was LibreOffice, but I don't see the same drop down list there now.  

Does anyone know a program that will let me change character coding on the fly?  I have titles for two of the files that I can give this guy.  But for the other two files, I have two titles each.  I suppose he'd figure out which was which, but if he wants to read the files, he'll need to know the character set, too.  I promise to make a note of the right set this time.  Can anyone help?

---

### Post by Rubi1200 on 2024-09-24
Would you be willing to provide us with a snippet of this "gibberish" so I can test how to convert?

Might be best to add it to a text document and attach to your post.

---

### Post by etonry on 2024-09-24
[FONT=Nimbus Roman]These are the file names of the files, as they appear in a directory, in English, followed by the characters of the title from the beginning of the document.
Habat1.txt                         äáú ùì äùëðéí[/FONT]

  [FONT=Nimbus Roman]hebrew1.txt                             ÷åøñ öéìåí îú÷ãí[/FONT]

  [FONT=Nimbus Roman]mill.txt                                äàéù äùååä îéìéåðéí        [/FONT] 

  [FONT=Nimbus Roman]telepath.txt                           äìåçù  ñéôåø ùìéèä èìàôèé îàú[/FONT]

I tried some different codes, but not in the same way I did it last time.  I'm not sure if that isn't my problem.  I may not have used them correctly.  I can give you more text, but this should be enough.

Thanks for a quick reply.

---

### Post by Rubi1200 on 2024-09-25
I struggled to find a way to do this in LibreOffice.

However, I found an online tool that will convert the string to Hebrew characters.

This is what you need to do:

go to this website: [https://string-functions.com/encodedecode.aspx](https://string-functions.com/encodedecode.aspx)

Enter the text, for example, Habat1.txt äáú ùì äùëðéí
In the dropdown menus for Encode and Decode use the following:
Encode = iso-8859-15
Decode = windows-1255

Click encode/decode and this is the result Habat1.txt &#1492;&#1489;&#1514; &#1513;&#1500; &#1492;&#1513;&#1499;&#1504;&#1497;&#1501;
[https://prnt.sc/LZ4UeDEylfh3](https://prnt.sc/LZ4UeDEylfh3)

Without knowing the rest of the file I would say the conversion is correct. Habat means the daughter and the converted text means the Neighbor's Daughter.

Hope this helps.

---

### Post by etonry on 2024-09-25
Thank you so very much!  This is perfect.  I got the same titles I had before,  I had two of the stories mixed up with the titles, but now I know which is which.  I can give this information to the friend so he can actually read these stories.  And I will save your instructions just in case I need them again.

---

### Post by Rubi1200 on 2024-09-25
Glad to hear it worked.

To help others find this solution, please mark your thread as Solved using the Thread Tools at the top of your first post.

Thanks.

---

### Post by grahammechanical on 2024-09-25
For anyone who wants to know - In Libreoffice Writer click the omega character &#937; then under Character block select basic Hebrew from the drop down menu. That we show all the characters in the Hebrew Aleph beth. The Hebrew names for the Greek alpha beta = alphabetRegards

---

### Post by etonry on 2024-09-25
I wasn't trying to write with Hebrew characters, I was trying to decipher the gibberish that hid the Hebrew characters.  Rubi1200 gave me just the exact help I needed.

---

