---
title: "Changes to text2pdf.py don't work"
date: 2019-04-13
forum: General Help
---

### Post by pedro_rodriguez2 on 2019-04-13
I am trying to convert text files to pdf. I want the pdf pagesize to be A5, landscape.

To my great surprise, I found the Python script text2pdf.py below on my laptop in: /home/pedro/.local/bin/ I can't remember ever downloading this. It probably comes with Ubuntu.

> pedro@pedro-newssd:~/getEmailDataSummer2019/18BE/text2pdf$ for i in /home/pedro/getEmailDataSummer2019/18BE/text2pdf/*.txt; do /home/pedro/.local/bin/text2pdf -o "$i".pdf "$i"; done
pedro@pedro-newssd:~/getEmailDataSummer2019/18BE/text2pdf$ 

It works fine after I set the linesize in line 49 manually to 130.

I changed line 10 to size = 8
I changed line 24 (it was orientation='portrait') to 

```
def make_pdf(afile, orientation='landscape', encoding='utf-8', point=(30, 20)):
```

so I would have landscape orientation, but I still get letter or A4, portrait.

I changed line 42. (It was A4) to:

```
printer.setPageSize(Qp.QPrinter.A5)
```

I still get A4 or letter, (not sure exactly) portrait.

**Does anyone know why the page format does not change??**

```
#!/usr/bin/python3
import os.path
import argparse
import PyQt5.QtWidgets as Qw
import PyQt5.QtGui as Qg
import PyQt5.QtPrintSupport as Qp


def best_font_size(linesize, pageRect, fontname, margin=5):
    size = 8
    while True:
        font = Qg.QFont(fontname, size)
        font_line_height = Qg.QFontMetrics(font).height()
        font_line_width = (Qg.QFontMetrics(font).width('A') * linesize)
        #print(int(pageRect.width() / Qg.QFontMetrics(font).width('A')))
        #print(int(pageRect.height() / Qg.QFontMetrics(font).height()))
        if pageRect.width() < font_line_width:
            size = size - 1
        else:
            break
    return size


def make_pdf(afile, orientation='landscape', encoding='utf-8', point=(30, 20)):
    """Create PDF from text

    :param afile: Text file to convert
    :param orientation: PDF orientation (lamdscape or portrait)
    :param encoding: The actual encoding of afile
    :param point: (column, row) start point
    """
    # fontname = "DejaVu Sans Mono"
    # fontname = "Monospace"
    fontname = "Ubuntu Mono"
    # fontname = "Liberation Mono"
    start_row, start_col = point
    with open(afile, encoding=encoding) as afi:
        lines = list(afi)
    *fname, _ = afile.split('.')
    fname = '.'.join(fname + ['pdf'])
    printer = Qp.QPrinter()
    printer.setPageSize(Qp.QPrinter.A5)
    printer.setOutputFileName(fname)
    printer.setOutputFormat(Qp.QPrinter.PdfFormat)
    if orientation == 'landscape':
        printer.setOrientation(Qp.QPrinter.Landscape)
    pageRect = printer.pageRect()
    #bestSize = best_font_size(
    #    max([len(i) for i in lines]), pageRect, fontname)
    bestSize = best_font_size(
        130, pageRect, fontname)
    font = Qg.QFont(fontname, bestSize)
    # font.setStyleHint(Qg.QFont.TypeWriter)
    font_line_height = Qg.QFontMetrics(font).height()
    painter = Qg.QPainter(printer)
    page = 1
    row = start_row
    for line in lines:
        painter.save()
        painter.setFont(font)
        row += font_line_height
        try:
            painter.drawText(start_col, row, line)
        except:
            painter.drawText(start_col, row, 'CodePage error !!!')
        if row > (pageRect.height() - 54):
            printer.newPage()
            row = start_row
        painter.restore()
    painter.end()


if __name__ == '__main__':
    pars = argparse.ArgumentParser(description='Convert text to pdf')
    pars.add_argument('file', help='Text FILE to be converted')
    pars.add_argument('-e', '--Encoding', help='Encoding of file')
    pars.add_argument('-o', '--Orientation', help='portrait or landscape')
    pars.add_argument('--version', action='version', version='0.1')
    args = pars.parse_args()
    if not os.path.isfile(args.file):
        print('No such file : %s' % args.file)
    else:
        app = Qw.QApplication([])
        ret = make_pdf(args.file, args.Orientation, args.Encoding)
```

---

### Post by oldfred on 2019-04-13
I was just playing with one of my old python programs and had issues. (shows C examples, but you can get idea).
[https://wiki.qt.io/Transition_from_Qt_4.x_to_Qt5](https://wiki.qt.io/Transition_from_Qt_4.x_to_Qt5)
Says change QtGui to QtWidgets in all places.
When I did that my little test program then worked.

There also is this:
[https://github.com/rferrazz/pyqt4topyqt5](https://github.com/rferrazz/pyqt4topyqt5)

---

### Post by dragonfly41 on 2019-04-14
There is also a document conversion tool Pandoc for many combinations of document conversions ..

[https://pandoc.org/MANUAL.html](https://pandoc.org/MANUAL.html)

Here is an example of code ..

pandoc test.txt -o test.pdf

---

### Post by pedro_rodriguez2 on 2019-04-14
Thanks to both of you!

pandoc looks very interesting. Do you know if it has a python module? If not I can call it with 

import subprocess

I'm discovering that pdfs are tricky customers.

fpdf lets me define my pdf well, but doesn't seem to use utf-8, so I can't display Chinese.

Anyway, thanks for the replies!

@dragonfly: I've got a font problem, any tips?

> pedro@pedro-school2:~/clozetexts$ pandoc BEIR1cloze.txt -o BEIR1cloze.pdf
! Font T1/cmr/m/n/10=ecrm1000 at 10.0pt not loadable: Metric (TFM) file not fou
nd.
<to be read again> 
relax 
l.105 \fontencoding\encodingdefault\selectfont

pandoc: Error producing PDF
pedro@pedro-school2:~/clozetexts$ 

Is there a pandoc --usefont myfont option??

Edit: stackoverflow to the rescue! This fixed it!

[https://stackoverflow.com/questions/22081991/rmarkdown-pandoc-pdflatex-not-found](https://stackoverflow.com/questions/22081991/rmarkdown-pandoc-pdflatex-not-found)

---

### Post by pedro_rodriguez2 on 2019-04-15
pandoc is great! Gives great control! Thanks a lot for the tip!

pandoc --variable=geometry:a5paper -V geometry:margin=0.5in -V geometry:landscape ILSU1GreenDesignHV1.txt -o ILSU1GreenDesignHV1.pdf

---

### Post by dragonfly41 on 2019-04-15
Yes, it is a superb tool. But of course a number of editors allow export to pdf.
Scribus is one such layout tool.  There are others.

---

