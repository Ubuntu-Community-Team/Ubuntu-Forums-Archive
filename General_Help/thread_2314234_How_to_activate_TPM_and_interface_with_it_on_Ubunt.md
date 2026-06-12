---
title: "How to activate TPM and interface with it on Ubuntu"
date: 2016-02-19
forum: General Help
---

### Post by shahin on 2016-02-19
I have am trying to interface with an external board connected to my Ubuntu box via USB. I found some procedures on how to interface with a trusted platform module. My board is a development board made by Atmel. I do know if I am doing the right things; the procedures stated to ```
modprobe tpm
```. Then I installed tcsd with ```
sudo apt-get install tcm
```. But I get the following errors: 
```
/lib/modules/4.2.0-16-generic/kernel/drivers/char/tpm$ tscd -f 
Xt Error: Cannot convert string "-*-helvetica-bold-r-*--12-*" to type FontStruct

Xt Error: Missing charsets in String to FontSet conversion

Xt Error: Cannot convert string "-*-helvetica-medium-r-*--10-*" to type FontSet

Xt Error: Cannot convert string "-*-helvetica-medium-r-*--10-*" to type FontStruct

Xt Error: Cannot convert string "-*-courier-medium-r-*--12-*" to type FontStruct

Usage: tscd [options] [document]
Options:
-drawing <w>x<h>	Create drawing area of <w>x<h> pixels
-h[elp]			Show this message and quit
-maxdrawing <w>x<h>	Set maximum drawing area size to <w>x<h> pixels
-projdir <dir>		Set the project directory to <dir>
-priv_cmap		Start the editor with a private colormap
-toPS [<file>.ps]	Generate PostScript (to <file>.ps or else stdout) and quit
-toEPS [<file>.eps]	Generate EPS (to <file>.eps or else stdout) and quit
-toFig [<file>.fig] [-latex]	Generate Fig format (to <file>.fig or else
			stdout) and quit. When the -latex option is given
			LaTeX fonts are generated, otherwise normal PostScript
			 fontsare generated
-toPNG <file>.png	Generate PNG format to <file>.png and quit
-v[ersion]		Show the TCM version and quit
remark: the -toXXX options require an existing TCM document file

```
Can anyone help me with the name of the packages I need to install to get rid of the errors above? 
I also want to ask what is the difference between ```
4.2.0-16-generic  4.2.0-27-generic
``` directories. There are a number of modules, which I may potentially need, and I want to know which ones I should activate. Why do these two directories exist? I did a fresh install of Ubuntu 15.4; seems like I have two different versions of the kernel on my machine?

---

