---
title: "Xerox pe120i network printer"
date: 2007-02-07
forum: General Help
---

### Post by westley.anderson on 2007-02-07
I am trying to set up a xerox pe 120i network printer in ubuntu. 

What i tried. 
adding a ipp network printer
a. clicked on system > administration > Printing
b. double clicked new printer
c. selected network printer, cups, and [http://10.2.4.1:631](http://10.2.4.1:631) as url
d. selected xerox and clciked install driver pointed to the pdd file i downloaded from the following link linux mfp driver
[http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=PE120_PE120I&Xlang=en_US&Xcntry=USA](http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=PE120_PE120I&Xlang=en_US&Xcntry=USA)

Finished the install and tried to test print and nothing happened

I just started using linux about a week ago so any advise in the simple terms and procedures  would be helpful

thanks in advance

wes

---

### Post by Hunding on 2007-02-23
I have been working on getting my PE120i to work as well. I am able to "see" the printer and can navigate to the web server located on my printer, and upload a print ready file, but I cannot figure out how to actually print a page, even a test page.
And if you could help me figure out how to scan through my network with it, I would certainly buy you a beer or three. :)

---

### Post by halitech on 2007-03-03
westley, when you are adding the printer, don't add the :631, just use 
```

http://10.2.4.1

```

and then browse to where you have the PPD file

Hundling,

acording to here

[http://office.support.xerox.com/SRVS/CGI-BIN/WEBCGI.cgi/,/?St=3,E=0000000000008288817,K=1886,Sxi=4,Case=obj(19517)]("http://office.support.xerox.com/SRVS/CGI-BIN/WEBCGI.cgi/,/?St=3,E=0000000000008288817,K=1886,Sxi=4,Case=obj(19517)")

the pe120/I is not capable of scanning over the network, only with a USB or Parallel cable connection. maybe follow the same steps as westley in regards to getting your unit to print over your network.

---

### Post by westley.anderson on 2007-08-18
Xerox printer worked with the following

[http://xxx.xxx.xxx.xxx/ipp](http://xxx.xxx.xxx.xxx/ipp) 
Replace the x's with the printers ip address
You also have to enable the ipp protocol in the xerox setup page
To get to the printers setup page type the printer ip address in a browser then select properties -> connectivity -> Protocols -> ipp click enable

---

