---
title: "Looking for software"
date: 2022-07-22
forum: General Help
---

### Post by marketou on 2022-07-22
May I ask here for advice to some software, running on Ubuntu? If not, please excuse me an delete my thread and if possible, give me advice, where to ask.

I am looking for this: On my phone I can not install more apps. So I want to turn the PHOTO of a written/printed document into a PDF on my PC. Just that,- not more. It should be like a scan with straight edges and if possible with a "paste and copy" - option for the written text afterwards. Any recommendations?

---

### Post by mikewhatever on 2022-07-22
You can ask any search engine with keywords like "ubuntu photo pdf".
Here is one result: [https://itsfoss.com/convert-multiple-images-pdf-ubuntu-1304/]("https://itsfoss.com/convert-multiple-images-pdf-ubuntu-1304/")

---

### Post by Paddy Landau on 2022-07-22
> **mikewhatever said:**
> Here is one result: [https://itsfoss.com/convert-multiple-images-pdf-ubuntu-1304/](https://itsfoss.com/convert-multiple-images-pdf-ubuntu-1304/)
The missing bit is the OP's request, "option for the written text afterwards", although I don't know what that means.

If the OP is asking how to add text to the PDF, you can use Xournal. You have three choices:

[LIST]
[*]Install Xournal (an older system) from the Universe repository:
```
sudo apt install xournal
```
Edit: Xournal++ is available from Ubuntu 22.04's repository:
```
sudo apt install xournalpp
```
[*]Install Xournal++ from snap:
```
snap install xournalpp
```
[*]Install Xournal++ from flatpak (if you have installed flatpak):
```
flatpak install com.github.xournalpp.xournalpp
```
[/LIST]
Xournal or Xournal++ takes a little getting used to, but it's easy to use.

An alternative method is to create a LibreOffice document, import each image as the background to a new page, and add text boxes or frames as required.

---

### Post by Impavidus on 2022-07-22
So you've got a picture/photograph/scan of a printed document and want to save it as a pdf file on your computer and be able to copy text from it. Right? The first part is trivial. Several tools can convert jpeg or whatever file format you use for your picture into pdf; image editors with a graphical interface or the convert command line tool:```
convert filename.jpeg filename.pdf
```
For the second part, being able to copy the text, you need optical character recognition or OCR. Look into that. Don't expect a 100% success rate.

---

### Post by Paddy Landau on 2022-07-22
> **Impavidus said:**
> … you need optical character recognition or OCR.
The OP doesn't make clear if that's what they need.

OCR has improved lately. To use it locally on your computer, try gImageReader:
```
sudo apt install tesseract-ocr tesseract-ocr-eng gimagereader
```
You also have to install any other language that's required, e.g. for French, tesseract-ocr-fra.

Or, you make use of free online services. If you have a Google account, try [Google Docs OCR]("https://support.google.com/drive/answer/176692?co=GENIE.Platform%3DDesktop&hl=en").

As Impavidus says, be prepared for errors!

---

### Post by Holger_Gehrke on 2022-07-22
+1 for tesseract. It's the best of the lot in my experience. There are graphical tools (gimagereader, gscan2pdf) that use tesseract as it's back-end. But you should always remember: a recognition rate of 99% means you get about one error every other line or worse.

Holger

---

### Post by dragonfly41 on 2022-07-22
Perhaps look for a service to extract text from a screenshot (if it is not sensitive data)

[https://brandfolder.com/workbench-suite](https://brandfolder.com/workbench-suite)

---

### Post by Paddy Landau on 2022-07-22
> **dragonfly41 said:**
> … extract text from a screenshot
Why not just upload the image itself, rather than taking a screenshot of the image and then uploading the screenshot? &#128533;

---

### Post by tea for one on 2022-07-22
Libre Office Writer > New Text Document > Copy Photo and Paste into document > Other editing as required > Export as PDF

---

