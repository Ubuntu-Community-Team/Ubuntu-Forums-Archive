---
title: "Plotting graphs on data"
date: 2016-03-09
forum: General Help
---

### Post by satimis on 2016-03-09
Plotting graphs on data

Hi all,

What will be the convenient way plotting graphs from data?

(Data example shown on attached file)

Thanks in advance

Regards
satimis

---

### Post by steeldriver on 2016-03-09
Depends what's convenient - to you

If the data is already in a spreadsheet of some sort, then most spreadsheet programs (LibreOffice 'Calc', Gnumeric, ...) have their own chart plotting features

If you want something more programatic (i.e. that you can automate with a script), there's gnuplot

---

### Post by dragonfly41 on 2016-03-09
You can try R Commander .. in Ubuntu Software Centre (and in Synaptic Package Manager as r-cran-rcmdr).

Here is just one useful tutorial for graphs. You will find many more if you search around.

[http://www.gardenersown.co.uk/education/lectures/r/graphs.htm](http://www.gardenersown.co.uk/education/lectures/r/graphs.htm)

---

### Post by satimis on 2016-03-09
> **steeldriver said:**
> Depends what's convenient - to you

If the data is already in a spreadsheet of some sort, then most spreadsheet programs (LibreOffice 'Calc', Gnumeric, ...) have their own chart plotting features
Thanks for your advice.

The data are on LibreOffice Writer.  Would it be possible converting them to graph?  If YES How?

> 
If you want something more programatic (i.e. that you can automate with a script), there's gnuplot
I heard gnuplot but without knowledge running it.

Before posting I found following links'
1)
Plot your graphs with command line gnuplot
[http://linux.byexamples.com/archives/487/plot-your-graphs-with-command-line-gnuplot/](http://linux.byexamples.com/archives/487/plot-your-graphs-with-command-line-gnuplot/)

2)
How Can I Create a Bell Curve of My Data
[http://answers.microsoft.com/en-us/office/forum/office_2007-excel/how-can-i-create-a-bell-curve-of-my-data/094f57c6-6442-e011-90b6-1cc1de79d2e2](http://answers.microsoft.com/en-us/office/forum/office_2007-excel/how-can-i-create-a-bell-curve-of-my-data/094f57c6-6442-e011-90b6-1cc1de79d2e2)

Regards
satimis

---

### Post by steeldriver on 2016-03-09
> **satimis said:**
> 
The data are on LibreOffice Writer.  Would it be possible converting them to graph?  If YES How?


It will depend what format the data are within Writer: is it as an *image* (like you have posted) or as actual text (for example in a table)?

If the former, then short of some kind of OCR-based solution, you really will need to type the numbers into the cells of a spreadsheet or a suitable text file manually

If the latter, you may be able to simply copy and paste the data into a spreadsheet or file.

---

### Post by satimis on 2016-03-09
> **steeldriver said:**
> It will depend what format the data are within Writer: is it as an *image* (like you have posted) or as actual text (for example in a table)?

If the former, then short of some kind of OCR-based solution, you really will need to type the numbers into the cells of a spreadsheet or a suitable text file manually

If the latter, you may be able to simply copy and paste the data into a spreadsheet or file.
Hi,

It is a text file .odt

Copy and paste didn't work.  The data were not pasted on the boxes under each column.

satimis

---

### Post by oldfred on 2016-03-09
Did you try paste special, that may give you more options.

And did you try copy and paste of just the data, the text info at top will probably make spreadsheet one column, where if it can see data columns it will then create columns which is what you want.

---

### Post by steeldriver on 2016-03-09
What are you trying to paste the content into?

Spreadsheet programs typically have quite good import 'wizards' that allow you to describe how your data are delimited and what rows/columns go where - but unless you can provide a minimal example (e.g. some data in the same format, saved as a single-page odt file) for us to try, you'll have to just figure out the exact procedure for yourself

---

### Post by satimis on 2016-03-09
> **oldfred said:**
> Did you try paste special, that may give you more options.

And did you try copy and paste of just the data, the text info at top will probably make spreadsheet one column, where if it can see data columns it will then create columns which is what you want.
Please refer to files attached

Screenshot_paste_special.png
Screenshot_paste.png

satimis

---

### Post by satimis on 2016-03-09
> **steeldriver said:**
> What are you trying to paste the content into?

Spreadsheet programs typically have quite good import 'wizards' that allow you to describe how your data are delimited and what rows/columns go where - but unless you can provide a minimal example (e.g. some data in the same format, saved as a single-page odt file) for us to try, you'll have to just figure out the exact procedure for yourself
Hi,

I found following youtube video;
LibreOffice: Calc- Importing Data - YouTube
[https://www.youtube.com/watch?v=GNSjDfL6tCI](https://www.youtube.com/watch?v=GNSjDfL6tCI)

.odt file can't be imported

satimis

---

### Post by mcgess on 2016-03-09
First thing make a slight change to your .odt file so that the time column always has a value similar to (red colour is just to emphasize the change you don't need to do that)

[TABLE]
[TR]
[TD="align: left"]01/03/2016[/TD]
[TD="align: left"]09.20am[/TD]
[TD="align: right"]129[/TD]
[TD="align: right"]75[/TD]
[TD="align: right"]58[/TD]
[TD="align: left"]right[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][COLOR=#ff0000]09.20am[/COLOR][/TD]
[TD="align: right"]132[/TD]
[TD="align: right"]81[/TD]
[TD="align: right"]71[/TD]
[TD="align: left"]right[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]12.15pm[/TD]
[TD="align: right"]129[/TD]
[TD="align: right"]76[/TD]
[TD="align: right"]69[/TD]
[TD="align: left"]right[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][COLOR=#ff0000]12.15pm[/COLOR][/TD]
[TD="align: right"]133[/TD]
[TD="align: right"]81[/TD]
[TD="align: right"]66[/TD]
[TD="align: left"]right[/TD]
[/TR]
[/TABLE]

Then save the file as a real text file (.txt) - LibreOffice text files have all sorts of extra information that you don't want here 
File > Save As > change the All Formats to Text (.txt) > Save

Close LibreOffice.

Right click on the new .txt file > Open with... > Installed Applications > Office > LibreOffice Calc
This should start a wizard which will allow you to control how calc reads the file.
Ensure that tab, space and merge delimiters are ticked

---

### Post by satimis on 2016-03-10
> **mcgess said:**
> First thing make a slight change to your .odt file so that the time column always has a value similar to (red colour is just to emphasize the change you don't need to do that)

[TABLE]
[TR]
[TD="align: left"]01/03/2016[/TD]
[TD="align: left"]09.20am[/TD]
[TD="align: right"]129[/TD]
[TD="align: right"]75[/TD]
[TD="align: right"]58[/TD]
[TD="align: left"]right[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][COLOR=#ff0000]09.20am[/COLOR][/TD]
[TD="align: right"]132[/TD]
[TD="align: right"]81[/TD]
[TD="align: right"]71[/TD]
[TD="align: left"]right[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]12.15pm[/TD]
[TD="align: right"]129[/TD]
[TD="align: right"]76[/TD]
[TD="align: right"]69[/TD]
[TD="align: left"]right[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][COLOR=#ff0000]12.15pm[/COLOR][/TD]
[TD="align: right"]133[/TD]
[TD="align: right"]81[/TD]
[TD="align: right"]66[/TD]
[TD="align: left"]right[/TD]
[/TR]
[/TABLE]

Then save the file as a real text file (.txt) - LibreOffice text files have all sorts of extra information that you don't want here 
File > Save As > change the All Formats to Text (.txt) > Save

Close LibreOffice.

Right click on the new .txt file > Open with... > Installed Applications > Office > LibreOffice Calc
This should start a wizard which will allow you to control how calc reads the file.
Ensure that tab, space and merge delimiters are ticked
Hi,

Your advice worked here.  Thanks

I attach the 1st page of the .odt file here.  It won't take me long time to input the data on a calc file because I just started creating the .odt file.

I expect creating following line charts on same diagram;
A line chart for SYS right arm
A line chart for SYS left arm
A line chart for DIA right arm
A line chart for DIA left arm
A line chart for Pulse right arm
A line chart for Pulse left arm

Regards
satimis

---

### Post by mcgess on 2016-03-10
I wish my blood pressure was as good as yours :(

---

