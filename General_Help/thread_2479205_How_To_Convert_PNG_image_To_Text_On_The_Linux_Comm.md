---
title: "How To Convert PNG image To Text On The Linux Command Line With OCR? (Ubuntu, Linux)"
date: 2022-09-18
forum: General Help
---

### Post by patrick2957672 on 2022-09-18
Hello,

I have a screenshot, made with scrot. (command :  sleep 1 ; scrot desktop.png).

How is it possible to convert the made PNG file to TEXT with OCR recognition?

Kind regards
Patrick

---

### Post by TheFu on 2022-09-18
gocr OR 

gscan2pdf or gscantopdf
I don't recall the name.  The image file can be loaded, then OCR applied and a PDF is created with the image "on top" and the text "under the image" inside the PDF.  You can go into the text layer and copy/paste that out.  Depending on the image quality and font, expect 70-95% accuracy for the text.  tesseract-ocr  is used by  gscantopdf, under the covers.

If you google "OCR linux", some other tools will be found. [https://help.ubuntu.com/community/OCR](https://help.ubuntu.com/community/OCR)
[https://www.howtogeek.com/682389/how-to-do-ocr-from-the-linux-command-line-using-tesseract/](https://www.howtogeek.com/682389/how-to-do-ocr-from-the-linux-command-line-using-tesseract/)

---

### Post by ajgreeny on 2022-09-18
I have used tesseract many times with great success though it does depend on the quality of the image you have so if it is possible to zoom the image you have before taking the scrot screenshot it may help get a better OCR output.

---

### Post by raleigh3 on 2022-09-18
```
#!/bin/bash
clear
[ -z "$1" ] && {
echo 
echo -e "Error!! NO PNG SPECIFIED. !!"
echo
echo -e "Convert png to text file."
echo 
echo -e "Image2File.sh [name of png file WITHOUT file extension.]"
echo
exit 1; }

convert "$1.png" "$1.tiff" &&
tesseract "$1.tiff" "$1"
rm *.tiff
```

---

