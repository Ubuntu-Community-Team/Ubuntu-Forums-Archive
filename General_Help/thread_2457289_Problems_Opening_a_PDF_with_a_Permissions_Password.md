---
title: "Problems Opening a PDF with a Permissions Password"
date: 2021-01-29
forum: General Help
---

### Post by ski-brimson on 2021-01-29
The document is protected with a permissions password according to Acrobat, but "Document Open Password" is set to no.

Firefox and Chrome can open the document.  I do not possess the password.

Which readers for Ubuntu besides Firefox and Chrome might work?

Okular asks for the password to open the document, as does Evince.

I need to preserve the data so I can do searches.  I do not wish to create another PDF with the text data stripped out.

---

### Post by HermanAB on 2021-01-29
Maybe open the PDF with a programmer's editor and delete the password stanza?

---

### Post by ajgreeny on 2021-01-29
If firefox can open it the same as other PDFs you can simply choose to  "Download" by clicking on the icon shown by the rather scruffy arrow in my screenshot and the save it again wherever you want.
It should be an exact copy of the file opened in firefox judging by what happened with a local PDF on my hard disk which I opened in firefox and saved again.
Both versions of the file had the same md5sum.

---

### Post by ski-brimson on 2021-02-01
I tried downloading with the download button inside the PDF viewer in Firefox, and with Okular I was solicited for a password.

How does one find and delete the password stanza?  This is a file of about 32MB.  I think gedit didn't like it.  I could use vim, but how does one find this?

grep -i password 49700_S.PDF 

  // Nothing found

---

### Post by ajgreeny on 2021-02-01
I still can not figure out how firefox mnages to open a password protected file for you but I thought I might have a possible answer by printing the file from firefox but not as a print on paper but using "Save as file", choosing pdf then simply using that saved version.

However, in my test the saved PDF is simply an image not a PDF with text, so it's not what you want, ansd even using **pdftotext** in terminal does not retrieve text from that image.

I wonder if pdftotext can retrieve text from a password protected file as it does from a non-protected one.  I don't have any that require a password but it may be worth your trying on your file.
```
pdftotext yourfile.pdf output-file.txt
```
Not much good for images needed in the file and the fonts etc will not be the same but I am grabbing at straws a bit here, hoping I might give you a clue or two.
The only other alternative I can think of is to open that file always with firefox where you can then still search the text easily.

---

### Post by HermanAB on 2021-02-02
Well, there is always vi and hexedit also...

---

### Post by ski-brimson on 2021-02-02
The key is supposed to prevent the file from being edited, not opened.  So there is probably some kind of hashing going on.

jklug@jklugDesk:~/JAK/NXP$ pdftotext 49700_S.PDF >49700_S.txt
Syntax Error: Invalid encryption key length
Command Line Error: Incorrect password

---

### Post by ski-brimson on 2021-02-02
Do you know of any keywords that might indicate a password stanza?  Remember that the password is to prevent update, not reading the document.

strings 49700_S.PDF | grep -i pass
  // Nothing returned

I suspect that it is the case that Firefox and Chrome have large teams of developers that need to keep up with the times, while Okular and Evince and texlive-binaries do not.

---

