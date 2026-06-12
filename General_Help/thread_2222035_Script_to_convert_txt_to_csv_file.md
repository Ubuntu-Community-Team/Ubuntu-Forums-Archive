---
title: "Script to convert txt to csv file"
date: 2014-05-04
forum: General Help
---

### Post by Ri_CatB_Support on 2014-05-04
Hi,

Can anyone  help me to write a script to convert the data present in .txt file needs to be converted to .csv or xls file.

after conversion i need to trigger a mail from the ubuntu server to my outlook.

Thanks in advance!

Regards,
Prakash

---

### Post by llamabr on 2014-05-04
Since csv is just a comma separates text file, that will be easy enough.  Do you just want a comma between every word?  Maybe a short example of your text file, and a more complete description would help here.

Or do you just want to change the name of the file from .txt to .csv?

---

### Post by tgalati4 on 2014-05-04
Check out csvtool.

```
sudo apt-get install csvtool
man csvtool
```

---

### Post by Ri_CatB_Support on 2014-05-05
Hi [**[COLOR=#000000]llamabr[/COLOR]**]("http://ubuntuforums.org/member.php?u=404864"),

Thanks for your headsup..
Actually im having one logs(i.e .txt file) which contains numeric values, which need to be put into excel sheet to do some average.

Can you please help me on this to write a script to put the txt file values into excel sheet.

Hope it clarifies you much better.

Thanks in anticipation!

Regards,
Prakash

---

### Post by llamabr on 2014-05-08
Probably we could help you, if we knew more about the file.  Maybe include a short sample, so we understand the form you want to change.

---

### Post by Ri_CatB_Support on 2014-05-11
The txt file contains value like:

120 ( only value)

These values need in an attachement(.csv or xls) through mail automatically.

Thanks in advance!

Regards,
Prakash

---

### Post by sudodus on 2014-05-11
> **Ri_CatB_Support said:**
> Hi [**[COLOR=#000000]llamabr[/COLOR]**]("http://ubuntuforums.org/member.php?u=404864"),

Thanks for your headsup..
Actually im having one logs(i.e .txt file) which contains numeric values, which need to be put into excel sheet to do some average.

Can you please help me on this to write a script to put the txt file values into excel sheet.

Hope it clarifies you much better.

Thanks in anticipation!

Regards,
Prakash

Try to import the file directly into Libre Office Calc or Microsoft Excel. It is likely to work without any previous conversion, at least if the numbers are separated by something (spaces, tabs etc) or if they are tabulated into consistent columns.

---

