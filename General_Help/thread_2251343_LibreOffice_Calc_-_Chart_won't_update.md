---
title: "LibreOffice Calc - Chart won't update"
date: 2014-11-03
forum: General Help
---

### Post by chaaderf on 2014-11-03
Hello!

I have a LibreOffice Calc document (.ods) and there is a chart where I have three different data series:

a) a column plot for data
b) a line plot for model 1
c) a line plot for model 2

The chart type: column and line

Until now, there haven't been any problems when I insert a new data but during this November, the chart just refuses to update itself. All other charts work fine, though. The only way to get the correct chart is delete the chart and recreate it. But as far as I know, it *should* update it just as fine as the other charts in the document. Could anyone give me a hint or two, what I should look for? I've tried to google this issue, but no success so far.

Thank you!

---

### Post by chaaderf on 2014-11-04
More details on this topic:

I tried to replace that problematic column and line type chart by a dot type chart. Everything worked - until I shut down the computer. After next boot the chart won't update anymore.

At this point I have tried:
[LIST]
[*]Force the update (F9 or Shift+Ctrl+F9)
[*]Turn on&off the autoupdate (Tools > Cell Content > Autoupdate)
[/LIST]

Today I found on google that sometimes there might be problems with different or wrong data type in columns. I rechecked (and applied the settings) that all my values are stored as general (Format > Cell > Number). We'll see if it works or not...

---

### Post by chaaderf on 2014-11-05
Okay. After boot the chart is again not working. -.-

---

### Post by coffeecat on 2014-11-06
*Thread moved to **General Help**.*

You'll be better off here. The Education and Science sub-forum is a "A place to discuss scientific and mathematics software for Ubuntu or linux in general."

---

### Post by amanchesterman on 2014-11-06
I've not encountered this problem myself so the first obvious question for me is whether your version of LibreOffice is up to date?

I use Xubuntu and have version 14.04.1: with that, the latest version of LibreOffice is 4.3.3.2. If you have the LibreOffice ppa enabled your version should update automatically, but it's worth checking.

A second obvious check is to ensure that you have Tools > Options > LibreOffice Calc > Updating set to 'always'.

I have read in the forums that odd/erratic behaviour of LibreOffice can often be cured by deleting your user profile and restarting the program, but I suggest you check the points I have suggested before you try that.

---

### Post by chaaderf on 2014-11-06
I have a version 4.2.7.2, installed in previous month. I tried to search about the ppa thing, but actually I didn't find anything related to that in places where I'd think it is... Where I should look to make sure that the correct ppa is enabled?

Also, I have had similar charts earlier, and they have worked like a charm... So I'm not sure how well the updating will work. But let's see. At least this version is coming EOL very soon.

Yes, I have enabled the 'always' setting - no change in behaving.

---

### Post by amanchesterman on 2014-11-07
Sorry, I can't tell you exactly how to check the ppa because I don't know which version of Ubuntu you are using. As I said in my post above, I use Xubuntu, and on that it's in Settings > Software and Updates > Other Software. If you have something called Software Updater you may be able to check through that also -- it's the app that ensures your machine downloads and installs regular updates.

Incidentally other users seem to report a similar problem from time to time: see here [http://en.libreofficeforum.org/node/1627](http://en.libreofficeforum.org/node/1627) I haven't had time to search through that forum to see if there are any answers to your question, but you might find it helpful to post your question on that forum (rather than here) because some of the posters there have vast experience of LibreOffice -- far more than a casual user like me.

---

