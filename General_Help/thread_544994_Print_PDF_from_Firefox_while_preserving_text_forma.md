---
title: "Print PDF from Firefox while preserving text formats"
date: 2007-09-07
forum: General Help
---

### Post by areteichi on 2007-09-07
I will try to be as clear as possible so that I can avoid any potential confusion and I won't be taken to be repeating what others have already asked (I hope I'm not). Just to make myself explicit, my issue is not about how to print to PDF from Firefox, but it is this: when I print a website to PDF from Firefox, all the texts and links are no longer recognized as such, i.e. the process by which PDF is composed basically turns everything into a single image saved as PDF in which text and links can no longer be recognized. I can still read everything from the original content, but I cannot hightlight and copy/paste texts of the PDF.

The only thread I could find that deals with a similar issue as mine was [[COLOR="Blue"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=140872") but the latest post was over a year ago and one of the solution that was mentioned (use Mozilla Suite to print PDF) in the thread doesn't seem proper given that the Mozilla Suite is no longer in development. I'm curious to know if anyone actually has a solution to this or if this problem is something I just have to wait for either Firefox developers to fix or cups-pdf to improve on its capability.

If anyone has a suggestion or solution, please let me know. Thanks in advance!

---

### Post by toylas on 2007-09-07
Hi

I did not know that you could save pdfs directly from firefox. I still can't find any option. Could you explain how you do it? I always print the file to ps and then convert it to pdf. And in that case it looks fine. I can not try to copy text as my acrobat installation is problematic (please see my post and let me know if you know a solution to my problem) but I don't think it saves it as an image. Please try to select text in the attached file. I made this pdf as I've described above.

Best,
Tulasi

---

### Post by FuturePilot on 2007-09-07
I tested that pdf and I cannot select text or anything with either Evince or Acrobat Reader. It's like it's being saved as an image and not as text.

---

### Post by areteichi on 2007-09-07
> **toylas said:**
> Hi

I did not know that you could save pdfs directly from firefox. I still can't find any option. Could you explain how you do it? I always print the file to ps and then convert it to pdf. And in that case it looks fine. I can not try to copy text as my acrobat installation is problematic (please see my post and let me know if you know a solution to my problem) but I don't think it saves it as an image. Please try to select text in the attached file. I made this pdf as I've described above.

Best,
Tulasi

[https://help.ubuntu.com/community/PDFPrinting?action=show&redirect=forum%2Fsoftware%2Fcups-pdf]("https://help.ubuntu.com/community/PDFPrinting?action=show&redirect=forum%2Fsoftware%2Fcups-pdf")

If you follow this procedure, you will get a virtual printer using cups-pdf; once you have that, you can just print as you would with any other printer, and the output PDF file will be created to /home/*/PDF.

Good luck.

---

### Post by areteichi on 2007-09-07
> **FuturePilot said:**
> I tested that pdf and I cannot select text or anything with either Evince or Acrobat Reader. It's like it's being saved as an image and not as text.

Right, that's exactly what I mean by "image". I hope someone can lead me to a solution.

---

### Post by grokwik on 2007-09-07
> **FuturePilot said:**
> I tested that pdf and I cannot select text or anything with either Evince or Acrobat Reader. It's like it's being saved as an image and not as text.

No offence but I can select text within this pdf... Using acrobat reader and windows XP (don't shout, I'm at work, I 've no choice :cry:)
[IMG]http://www.grokwik.com/toto/try.jpg[/IMG]

---

### Post by areteichi on 2007-09-07
> **grokwik said:**
> No offence but I can select text within this pdf... Using acrobat reader and windows XP (don't shout, I'm at work, I 've no choice :cry:)


Wow, I never would have guessed that the problem may have to do with a client program. I will install Acrobat for Linux and see how that will turn out. Thanks for letting us know

---

### Post by areteichi on 2007-09-09
Okay, you're right about being able to highlight/select PDFs in Acrobat (I tried for Linux), and that's certainly better than nothing. But now, there seems to be a problem copying and pasting texts from these PDFs; when I paste them, the texts are all garbled and illegible.
Do you have any idea as to why this is happening? Some possibilities might be that the version for Linux is outdated (Acrobat 7) or fonts aren't saved within the PDF file such that when I paste them, fonts aren't available.

---

### Post by noynac on 2007-09-10
> **byagietera said:**
> Okay, you're right about being able to highlight/select PDFs in Acrobat (I tried for Linux), and that's certainly better than nothing. But now, there seems to be a problem copying and pasting texts from these PDFs; when I paste them, the texts are all garbled and illegible.
I have the same problem. For example, I printed a web page to a PDF document using cups-pdf. I then opened this document in Acrobat Reader and selected and copied a few words of text. I pasted this text into gedit and got the following weird characters:





I am able to copy and paste text from downloaded manuals and other documents without a problem. So, it appears that the problem is with cups-pdf.

---

### Post by areteichi on 2007-09-12
I guess there is no solution to this issue besides waiting for cups-pdf to improve isn't there? :(

---

