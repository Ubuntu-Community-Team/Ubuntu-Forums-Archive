---
title: "Print foul up - Help needed !"
date: 2018-02-02
forum: General Help
---

### Post by Timmoore001 on 2018-02-02
My otherwise fine version of Ubuntu 16.04 and my accidental miss keying resulted in 450 requests to print the front page of a manual !

Now I can delete each one ! but I don't want to spend x hours doing that !  The printer is a Samsung laser ML-3051N

So at the moment I can't print anything effectively nuking my printer !  A major pain ! 

Does anyone know how to delete the contents of the 'to be printed buffer ' ?

A thoughts would be very greatly appreciated !

A hair tearing,  *LOL*

Tim

---

### Post by kurt18947 on 2018-02-02
You could look at 'printers' - windows key then type "printers". You may see a list of print jobs and can cancel it/them. It depends a little on which 'flavor' of Ubuntu you have. I'm using Ubuntu Gnome 16.04 and it has the Gnome printers app by default. I prefer the app used by Xubuntu & Lubuntu among others so installed it from the repository. My preferred printer app is called "system-config-printer" and gives more options and control than the default Gnome app.

---

### Post by dragonfly41 on 2018-02-02
Do you have CUPS installed?

[https://help.ubuntu.com/lts/serverguide/cups.html](https://help.ubuntu.com/lts/serverguide/cups.html)

Then just launch [http://localhost:631/admin](http://localhost:631/admin)
and
[http://localhost:631/jobs/?](http://localhost:631/jobs/?) to clear jobs list.

---

### Post by Timmoore001 on 2018-02-02
Many thanks for responding......:  ))))

I may be a bit thick but I tried from Bash:-

sudo apt-get install system-config-printer

it did quite a lot of things   but didn't empty the buffer.

I think I missed understanding what I should do..

Thanks again , any more thoughts ?

Tim

---

### Post by Timmoore001 on 2018-02-02
Quote;-

Do you have CUPS installed?

[https://help.ubuntu.com/lts/serverguide/cups.html](https://help.ubuntu.com/lts/serverguide/cups.html)

Then just launch [http://localhost:631/admin](http://localhost:631/admin)
and
[http://localhost:631/jobs/?](http://localhost:631/jobs/?) to clear jobs list. 				

end Quote

I'll try this...

Many thanks for responding !

:  )))

Tim

---

### Post by Timmoore001 on 2018-02-02
Worked fine and got inside cups but....

***

[TABLE="class: inset"]
[TR]
[TD="width: 50%"][/TD]
 	[TD="width: 50%"]
[/TD]
[/TR]
[/TABLE]
 	[TABLE="class: list"]
  [TR]
[TH]ID[/TH]
[TH]Name[/TH]
[TH]User[/TH]
[TH]Size[/TH]
[TH]Pages[/TH]
[TH]State[/TH]
[TH]Control[/TH]
[/TR]
    [TR]
 [TD][ML-3050]("http://localhost:631/printers/ML-3050")-1047 [/TD]
 [TD]Unknown [/TD]
 [TD]Withheld [/TD]
 [TD]340k [/TD]
 [TD]Unknown [/TD]
 [TD]pending since
Thu 01 Feb 2018 10:29:09 GMT [/TD]
 [TD]     
[/TD]
[/TR]
[/TABLE]
    [TABLE="class: list"]
[TR]
[TD]  [/TD]
 [/TR]
  [TR]
 [TD][ML-3050]("http://localhost:631/printers/ML-3050")-1048 [/TD]
 [TD]Unknown [/TD]
 [TD]Withheld [/TD]
 [TD]340k [/TD]
 [TD]Unknown [/TD]
 [TD]pending since
Thu 01 Feb 2018 10:29:09 GMT [/TD]
 [TD]     
[/TD]
[/TR]
[/TABLE]
      

was the result   under Control     'Hold Job /  Cancel /Move Job/

now it asked for a User Name and password..but nothing responded .....

I'll feel that I'm 99% of the way there but just need the last stage....

:  )))

Many thanks but the last bit is still needed

:  )))

Tim

---

### Post by dragonfly41 on 2018-02-02
I don't know how to clear your CUPS cache other than using Jobs Clear button.

I suggest that you also look at System Settings > Printer

Click on your Printer icon.

Check Policies are all ticked.

...

Also research using CUPS command line ...

lpc status

[https://current.workingdirectory.net/posts/2013/cups-cli-admin/](https://current.workingdirectory.net/posts/2013/cups-cli-admin/)

Dig around further for commands

[https://askubuntu.com/questions/350334/how-do-i-clear-a-print-queue-in-ubuntu](https://askubuntu.com/questions/350334/how-do-i-clear-a-print-queue-in-ubuntu)

And here of course ...

[http://localhost:631/help/options.html](http://localhost:631/help/options.html)


[Later edit]

I am adding some notes on exploring log files.

First install glogg which is a log file viewer.

```
sudo apt-get update && sudo apt-get install glogg
```

You may already have another log file viewer installed by I prefer glogg.

Now run glogg and navigate to the CUPS log files found here ...

/var/log/cups/

---

### Post by raleigh3 on 2018-02-02
I went to /var/log/cups/ and deleted the log files yet cups still shows them with Show all jobs?

---

### Post by Geoffrey_Arndt on 2018-02-02
Try this:

In browser url field:   
>  [COLOR=#0000ff]localhost:631/printers[/COLOR] <enter>
Choose the printer you want to manage (delete jobs etc.)
>  [COLOR=#0000ff]Workforce-645[/COLOR]
Click on the "[COLOR=#0000ff]Maintenance[/COLOR]" button to see the dropdown selections, and select "[COLOR=#0000ff]cancel all jobs[/COLOR]"

---

### Post by raleigh3 on 2018-02-02
Afraid it does not work.

Printer works fine otherwise.

---

### Post by HermanAB on 2018-02-03
Three ways:
There is a cancel command, a lprm command, or when all else fails, you can manually rm everything in the cache and then restart CUPS.

1. [https://www.garron.me/en/go2linux/clean-cancel-printer-queue-linux.html](https://www.garron.me/en/go2linux/clean-cancel-printer-queue-linux.html)

2. [https://www.garron.me/en/go2linux/clean-cancel-printer-queue-linux.html](https://www.garron.me/en/go2linux/clean-cancel-printer-queue-linux.html)

---

### Post by oldos2er on 2018-02-03
> **raleigh3 said:**
> Afraid it does not work.

Printer works fine otherwise.

Please don't hijack other people's threads; it's rude (it's the online equivalent of interrupting others' conversations). Always start your own thread; you may link to other threads if you feel the need to.

---

### Post by Timmoore001 on 2018-02-03
I have at last got the printer working again, by deleting each of the 450 print request manually.   Not the way I wanted to do it but I needed a working printer.

May I thank everybody who made many very interesting suggestions, which I greatly appreciated.   There must be a simple way of flushing data buffers.

Forums are vital for the Linux world IMHO !

So thanks again.

:  )

Tim

---

### Post by oldos2er on 2018-02-03
Great! Would you please mark your thread 'Solved' under Thread Tools at the top of the page? It helps others with similar problems. Thanks.

---

### Post by Timmoore001 on 2018-02-04
I found a way of using the 3 little windows to be within 2 to 3mm in the ubuntu 'printer' top of screen options which vastly reduced the mouse movements to it came a lot faster to manually delete each of the 450 instances of 'print' requests.

This made it significantly easier to deal with.  A lateral thought worked out..  Phew. (desperation is the mother of invention ?  *LOL* )

:  )))

Tim

---

### Post by HermanAB on 2018-02-04
Well, you could also have used a macro scripting tool like AutoKey.  It is in the repos!

---

### Post by Geoffrey_Arndt on 2018-02-05
> **Timmoore001 said:**
> I have at last got the printer working again, by deleting each of the 450 print request manually.   Not the way I wanted to do it but I needed a working printer.

May I thank everybody who made many very interesting suggestions, which I greatly appreciated.   [U][B]There must be a simple way of flushing data buffers.
[/B][/U]
Forums are vital for the Linux world IMHO !

So thanks again.

:  )

Tim

There is . . . via CUPS - - it's called "Cancel ALL Jobs" and is accessed via "localhost:631/printers", then select your printer, then click on maintenance, and finally select "Cancel all Jobs" from that drop down menu.

---

