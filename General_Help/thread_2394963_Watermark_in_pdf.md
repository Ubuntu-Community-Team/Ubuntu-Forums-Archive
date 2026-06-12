---
title: "Watermark in pdf"
date: 2018-06-24
forum: General Help
---

### Post by AnupamMitra on 2018-06-24
I would like to know whether it is possible to remove watermark from a PDF document which irritates me much. My O/S is Ubuntu 16.04 (64 Bit).

---

### Post by #&amp;thj^% on 2018-06-24
I have used this method with pdftk have a look: [https://superuser.com/questions/448519/how-to-remove-watermark-from-pdf-using-pdftk](https://superuser.com/questions/448519/how-to-remove-watermark-from-pdf-using-pdftk)

---

### Post by AnupamMitra on 2018-06-24
> **1fallen said:**
> I have used this method with pdftk have a look: [https://superuser.com/questions/448519/how-to-remove-watermark-from-pdf-using-pdftk](https://superuser.com/questions/448519/how-to-remove-watermark-from-pdf-using-pdftk)

Thanks for your reply. Actually, I have tried to apply this one, but something might have wrong. 

```

anupam@anupam-ubuntu:~$ sed -e "s/watermarktextstring/ /g" <input.pdf >unwatermarked.pdf
bash: input.pdf: No such file or directory
anupam@anupam-ubuntu:~$ 

```

I failed to proceed and/or understand further due to my ignorance.

---

### Post by linux4me on 2018-06-24
The command you'll need to run, according to that link, is:
```
sed -e "s/watermarktextstring/ /g" <input.pdf >unwatermarked.pdf && pdftk unwatermarked.pdf output fixed.pdf && mv fixed.pdf unwatermarked.pdf
```
In order to use it, you need to run the command from the folder where the original PDF is located, and replace the "watermarktextstring" with the text string of the watermark in your PDF, and "input.pdf" with the name of the original PDF. That's what the error was trying to tell you; it couldn't find a file called "input.pdf" in the folder where you were working.

---

### Post by #&amp;thj^% on 2018-06-24
> **linux4me said:**
> The command you'll need to run, according to that link, is:
```
sed -e "s/watermarktextstring/ /g" <input.pdf >unwatermarked.pdf && pdftk unwatermarked.pdf output fixed.pdf && mv fixed.pdf unwatermarked.pdf
```
In order to use it, you need to run the command from the folder where the original PDF is located, and replace the "watermarktextstring" with the text string of the watermark in your PDF, and "input.pdf" with the name of the original PDF. That's what the error was trying to tell you; it couldn't find a file called "input.pdf" in the folder where you were working.

+1^^^^
I'm sorry I had an event today that I needed to leave for. :)
linux4me gives you the correct naming and procedure to get this accomplished.
If you are still having problems, perhaps give us the location and the whole name of the PDF.
EDIT: It would also be a good idea to have a backup copy of the PDF you are working on just for the event of another error. (i hope that makes sense)

---

### Post by AnupamMitra on 2018-06-26
> **linux4me said:**
> The command you'll need to run, according to that link, is:
```
sed -e "s/watermarktextstring/ /g" <input.pdf >unwatermarked.pdf && pdftk unwatermarked.pdf output fixed.pdf && mv fixed.pdf unwatermarked.pdf
```
In order to use it, you need to run the command from the folder where the original PDF is located, and replace the "watermarktextstring" with the text string of the watermark in your PDF, and "input.pdf" with the name of the original PDF. That's what the error was trying to tell you; it couldn't find a file called "input.pdf" in the folder where you were working.

Regret for my ignorance. 
Location of the file is on my desktop. I think it would be "/home/anupam/Desktop". Isn't it? If so, would it be like this ?  

sed /home/anupam/Desktop "s/watermarktextstring/ /g" <input.pdf >unwatermarked.pdf  && pdftk unwatermarked.pdf output fixed.pdf && mv  fixed.pdf unwatermarked.pdf

---

### Post by AnupamMitra on 2018-06-26
> **1fallen said:**
> +1^^^^
I'm sorry I had an event today that I needed to leave for. :)
linux4me gives you the correct naming and procedure to get this accomplished.
If you are still having problems, perhaps give us the location and the whole name of the PDF.
EDIT: It would also be a good idea to have a backup copy of the PDF you are working on just for the event of another error. (i hope that makes sense)

Sorry for the trouble.
The file is on my desktop and the name of the file is "test.pdf".

---

### Post by linux4me on 2018-06-26
If the file is on your Desktop, you can just open a Terminal session, then run:
```
cd Desktop/
```
to change to your Desktop folder. 

It might be easier to understand the rest if you break the three commands down and deal with them one at a time. The "&&" in the original command is just joining three different commands.

The first command uses a program called sed to replace the watermark text in the original PDF. In order for it to do that, you need to tell sed what text to replace, and which PDF is your input (original) PDF. To do that, replace "watermarktextstring" in the command with the actual text of the watermark in your PDF, and replace "input.pdf" in the command with the actual file name of your PDF. So if your PDF is called "mypdf.pdf" and the watermark text is "MyWatermark", you'd run the command:
```
sed -e "s/MyWatermark/ /g" <mypdf.pdf >unwatermarked.pdf
```
According to the original link, the second command uses pdftk to fix the damage caused by removing the watermark text and rebuild the PDF:
```
pdftk unwatermarked.pdf output fixed.pdf
```
The final command simply renames the rebuilt PDF (fixed.pdf) to unwatermarked.pdf:
```
mv fixed.pdf unwatermarked.pdf
```
The file unwatermarked.pdf will be your final product.

---

### Post by AnupamMitra on 2018-06-26
> **linux4me said:**
> If the file is on your Desktop, you can just open a Terminal session, then run:
```
cd Desktop/
```
to change to your Desktop folder. 

It might be easier to understand the rest if you break the three commands down and deal with them one at a time. The "&&" in the original command is just joining three different commands.

The first command uses a program called sed to replace the watermark text in the original PDF. In order for it to do that, you need to tell sed what text to replace, and which PDF is your input (original) PDF. To do that, replace "watermarktextstring" in the command with the actual text of the watermark in your PDF, and replace "input.pdf" in the command with the actual file name of your PDF. So if your PDF is called "mypdf.pdf" and the watermark text is "MyWatermark", you'd run the command:
```
sed -e "s/MyWatermark/ /g" <mypdf.pdf >unwatermarked.pdf
```
According to the original link, the second command uses pdftk to fix the damage caused by removing the watermark text and rebuild the PDF:
```
pdftk unwatermarked.pdf output fixed.pdf
```
The final command simply renames the rebuilt PDF (fixed.pdf) to unwatermarked.pdf:
```
mv fixed.pdf unwatermarked.pdf
```
The file unwatermarked.pdf will be your final product.

Thanks for taking all the pains. Your step by step guidelines helped me a lot to follow the entire procedure. This time there was no problem to bring out the final product. 

However, the watermark of my pdf file could not be removed. Most probably the nature of the watermark is the main crux!

Thank you again.

---

