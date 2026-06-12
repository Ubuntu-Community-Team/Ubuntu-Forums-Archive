---
title: "Eterm font help"
date: 2007-07-12
forum: General Help
---

### Post by RichJacot on 2007-07-12
Hello,

I have been playing with Eterm and have found the setup I like with the exception of the font.  With the background I have I need a bolder font.  

Can someone point me in the right direction or let me know how to figure out how to change the fonts?

I'm currently excuting:

```
Eterm --geometry 150x75+50+40 --trans=true --borderless --scrollbar=true --buttonbar=false -f green --cmod 400 -c green --font-fx none --tint grey50
```

I'd like a little bit bigger font and bolder than what I'm getting with the above command.

---

### Post by jyba on 2007-07-12
I had a look through the Eterm themes and quite a lot of them use "-adobe-helvetica-medium-r-normal--10-100-75-75-p-56-iso8859-1". It's a bit wide but at least it's more legible than the default.

```
Eterm --geometry 100x75+50+40 --trans=true --borderless --scrollbar=true --buttonbar=false -f green --cmod 400 -c green --font-fx none --tint grey50 --font "-adobe-helvetica-medium-r-normal--10-100-75-75-p-56-iso8859-1"
```

---

### Post by RichJacot on 2007-07-13
Where did you get or how did you figure out "-adobe-helvetica-medium-r-normal--10-100-75-75-p-56-iso8859-1"?

A long while ago I found a website where you could pick a font you liked (size, style, etc) and it would give you a line like I put above.   Is anyone familiar with what I'm talking about?

---

### Post by jyba on 2007-07-13
I was afraid you'd ask that. :lolflag:It's something that I haven't got around to studying yet so I'm completely out of my depth here. I didn't figure it out, I just 'grep'ed for 'font' in Eterm's theme.cfg files like this...
```
grep 'font' /usr/share/Eterm/themes/*/theme.cfg
```
... and then experimented with the results. I too would like to know where Eterm searches for it's fonts and what the format "-adobe-helvetica-medium-r-normal--10-100-75-75-p-56-iso8859-1" means.

If anyone reading this can answer these questions, please do so.

When I was googling about this, after your second message, I managed to accumulate this list of fonts which you might like to experiment with in Eterm. 

```
-adobe-helvetica-bold-r-normal--8-80-75-75-p-50-iso8859-1"
-adobe-helvetica-bold-r-normal--10-100-75-75-p-60-iso8859-1"
-adobe-helvetica-bold-r-normal--12-120-75-75-p-70-iso8859-1"
-adobe-helvetica-bold-r-normal--14-140-75-75-p-82-iso8859-1"
-adobe-helvetica-bold-r-normal--18-180-75-75-p-103-iso8859-1"
-adobe-helvetica-bold-r-normal--24-240-75-75-p-138-iso8859-1"

-adobe-helvetica-medium-o-normal--8-80-75-75-p-47-iso8859-1"
-adobe-helvetica-medium-o-normal--10-100-75-75-p-57-iso8859-1"
-adobe-helvetica-medium-o-normal--12-120-75-75-p-67-iso8859-1"
-adobe-helvetica-medium-o-normal--14-140-75-75-p-78-iso8859-1"
-adobe-helvetica-medium-o-normal--18-180-75-75-p-98-iso8859-1"
-adobe-helvetica-medium-o-normal--24-240-75-75-p-130-iso8859-1"

-adobe-helvetica-medium-r-normal--8-80-75-75-p-46-iso8859-1"
-adobe-helvetica-medium-r-normal--10-100-75-75-p-56-iso8859-1"
-adobe-helvetica-medium-r-normal--12-120-75-75-p-67-iso8859-1"
-adobe-helvetica-medium-r-normal--14-140-75-75-p-77-iso8859-1"
-adobe-helvetica-medium-r-normal--18-180-75-75-p-98-iso8859-1"
-adobe-helvetica-medium-r-normal--24-240-75-normal (R), italic (I)

-Bitstream-Charter-Medium-R-Normal--11-80-100-100-P-61-ISO8859-1
-Bitstream-Charter-Medium-R-Normal--14-100-100-100-P-78-ISO8859-1
-Bitstream-Charter-Medium-R-Normal--17-120-100-100-P-95-ISO8859-1
-Bitstream-Charter-Medium-R-Normal--19-140-100-100-P-106-ISO8859-1
-Bitstream-Charter-Medium-R-Normal--25-180-100-100-P-139-ISO8859-1
-Bitstream-Charter-Medium-R-Normal--33-240-100-100-P-183-ISO8859-1
-Bitstream-Charter-Medium-I-Normal--11-80-100-100-P-60-ISO8859-1
-Bitstream-Charter-Medium-I-Normal--14-100-100-100-P-76-ISO8859-1
-Bitstream-Charter-Medium-I-Normal--17-120-100-100-P-92-ISO8859-1
-Bitstream-Charter-Medium-I-Normal--19-140-100-100-P-103-ISO8859-1
-Bitstream-Charter-Medium-I-Normal--25-180-100-100-P-136-ISO8859-1
-Bitstream-Charter-Medium-I-Normal--33-240-100-100-P-179-ISO8859-1

--------------------------------------------------------------------
Courier

normal (R), oblique (O), bold (B), bold oblique (BO)

-Adobe-Courier-Medium-R-Normal--11-80-100-100-M-60-ISO8859-1
-Adobe-Courier-Medium-R-Normal--14-100-100-100-M-90-ISO8859-1
-Adobe-Courier-Medium-R-Normal--17-120-100-100-M-100-ISO8859-1
-Adobe-Courier-Medium-R-Normal--20-140-100-100-M-110-ISO8859-1
-Adobe-Courier-Medium-R-Normal--25-180-100-100-M-150-ISO8859-1
-Adobe-Courier-Medium-R-Normal--34-240-100-100-M-200-ISO8859-1
-Adobe-Courier-Medium-O-Normal--11-80-100-100-M-60-ISO8859-1
-Adobe-Courier-Medium-O-Normal--14-100-100-100-M-90-ISO8859-1
-Adobe-Courier-Medium-O-Normal--17-120-100-100-M-100-ISO8859-1
-Adobe-Courier-Medium-O-Normal--20-140-100-100-M-110-ISO8859-1
-Adobe-Courier-Medium-O-Normal--25-180-100-100-M-150-ISO8859-1
-Adobe-Courier-Medium-O-Normal--34-240-100-100-M-200-ISO8859-1
-Adobe-Courier-Bold-R-Normal--11-80-100-100-M-60-ISO8859-1
-Adobe-Courier-Bold-R-Normal--14-100-100-100-M-90-ISO8859-1
-Adobe-Courier-Bold-R-Normal--17-120-100-100-M-100-ISO8859-1
-Adobe-Courier-Bold-R-Normal--20-140-100-100-M-110-ISO8859-1
-Adobe-Courier-Bold-R-Normal--25-180-100-100-M-150-ISO8859-1
-Adobe-Courier-Bold-R-Normal--34-240-100-100-M-200-ISO8859-1
-Adobe-Courier-Bold-O-Normal--11-80-100-100-M-60-ISO8859-1
-Adobe-Courier-Bold-O-Normal--14-100-100-100-M-90-ISO8859-1
-Adobe-Courier-Bold-O-Normal--17-120-100-100-M-100-ISO8859-1
-Adobe-Courier-Bold-O-Normal--20-140-100-100-M-110-ISO8859-1
-Adobe-Courier-Bold-O-Normal--25-180-100-100-M-150-ISO8859-1
-Adobe-Courier-Bold-O-Normal--34-240-100-100-M-200-ISO8859-1

--------------------------------------------------------------------
Helvetica

normal (R), oblique (O), bold (B), bold oblique (BO)

-Adobe-Helvetica-Medium-R-Normal--11-80-100-100-P-56-ISO8859-1
-Adobe-Helvetica-Medium-R-Normal--14-100-100-100-P-76-ISO8859-1
-Adobe-Helvetica-Medium-R-Normal--17-120-100-100-P-88-ISO8859-1
-Adobe-Helvetica-Medium-R-Normal--20-140-100-100-P-100-ISO8859-1
-Adobe-Helvetica-Medium-R-Normal--25-180-100-100-P-130-ISO8859-1
-Adobe-Helvetica-Medium-R-Normal--34-240-100-100-P-176-ISO8859-1
-Adobe-Helvetica-Medium-O-Normal--11-80-100-100-P-57-ISO8859-1
-Adobe-Helvetica-Medium-O-Normal--14-100-100-100-P-78-ISO8859-1
-Adobe-Helvetica-Medium-O-Normal--17-120-100-100-P-88-ISO8859-1
-Adobe-Helvetica-Medium-O-Normal--20-140-100-100-P-98-ISO8859-1
-Adobe-Helvetica-Medium-O-Normal--25-180-100-100-P-130-ISO8859-1
-Adobe-Helvetica-Medium-O-Normal--34-240-100-100-P-176-ISO8859-1
-Adobe-Helvetica-Bold-R-Normal--11-80-100-100-P-60-ISO8859-1
-Adobe-Helvetica-Bold-R-Normal--14-100-100-100-P-82-ISO8859-1
-Adobe-Helvetica-Bold-R-Normal--17-120-100-100-P-92-ISO8859-1
-Adobe-Helvetica-Bold-R-Normal--20-140-100-100-P-105-ISO8859-1
-Adobe-Helvetica-Bold-R-Normal--25-180-100-100-P-138-ISO8859-1
-Adobe-Helvetica-Bold-R-Normal--34-240-100-100-P-182-ISO8859-1
-Adobe-Helvetica-Bold-O-Normal--11-80-100-100-P-60-ISO8859-1
-Adobe-Helvetica-Bold-O-Normal--14-100-100-100-P-82-ISO8859-1
-Adobe-Helvetica-Bold-O-Normal--17-120-100-100-P-92-ISO8859-1
-Adobe-Helvetica-Bold-O-Normal--20-140-100-100-P-103-ISO8859-1
-Adobe-Helvetica-Bold-O-Normal--25-180-100-100-P-138-ISO8859-1
-Adobe-Helvetica-Bold-O-Normal--34-240-100-100-P-182-ISO8859-1

--------------------------------------------------------------------
Lucida

normal (RS), italic (IS), bold (BS), bold italic (BIS)

-B&H-Lucida-Medium-R-Normal-Sans-11-80-100-100-P-63-ISO8859-1
-B&H-Lucida-Medium-R-Normal-Sans-14-100-100-100-P-80-ISO8859-1
-B&H-Lucida-Medium-R-Normal-Sans-17-120-100-100-P-96-ISO8859-1
-B&H-Lucida-Medium-R-Normal-Sans-20-140-100-100-P-114-ISO8859-1
-B&H-Lucida-Medium-R-Normal-Sans-25-180-100-100-P-142-ISO8859-1
-B&H-Lucida-Medium-R-Normal-Sans-26-190-100-100-P-147-ISO8859-1
-B&H-Lucida-Medium-R-Normal-Sans-34-240-100-100-P-191-ISO8859-1
-B&H-Lucida-Medium-I-Normal-Sans-11-80-100-100-P-62-ISO8859-1
-B&H-Lucida-Medium-I-Normal-Sans-14-100-100-100-P-80-ISO8859-1
-B&H-Lucida-Medium-I-Normal-Sans-17-120-100-100-P-97-ISO8859-1
-B&H-Lucida-Medium-I-Normal-Sans-20-140-100-100-P-114-ISO8859-1
-B&H-Lucida-Medium-I-Normal-Sans-25-180-100-100-P-141-ISO8859-1
-B&H-Lucida-Medium-I-Normal-Sans-26-190-100-100-P-147-ISO8859-1
-B&H-Lucida-Medium-I-Normal-Sans-34-240-100-100-P-192-ISO8859-1
-B&H-Lucida-Bold-I-Normal-Sans-11-80-100-100-P-69-ISO8859-1
-B&H-Lucida-Bold-I-Normal-Sans-14-100-100-100-P-90-ISO8859-1
-B&H-Lucida-Bold-I-Normal-Sans-17-120-100-100-P-108-ISO8859-1
-B&H-Lucida-Bold-I-Normal-Sans-20-140-100-100-P-127-ISO8859-1
-B&H-Lucida-Bold-I-Normal-Sans-25-180-100-100-P-159-ISO8859-1
-B&H-Lucida-Bold-I-Normal-Sans-26-190-100-100-P-166-ISO8859-1
-B&H-Lucida-Bold-I-Normal-Sans-34-240-100-100-P-215-ISO8859-1
-B&H-Lucida-Bold-R-Normal-Sans-11-80-100-100-P-70-ISO8859-1
-B&H-Lucida-Bold-R-Normal-Sans-14-100-100-100-P-89-ISO8859-1
-B&H-Lucida-Bold-R-Normal-Sans-17-120-100-100-P-108-ISO8859-1
-B&H-Lucida-Bold-R-Normal-Sans-20-140-100-100-P-127-ISO8859-1
-B&H-Lucida-Bold-R-Normal-Sans-25-180-100-100-P-158-ISO8859-1
-B&H-Lucida-Bold-R-Normal-Sans-26-190-100-100-P-166-ISO8859-1
-B&H-Lucida-Bold-R-Normal-Sans-34-240-100-100-P-216-ISO8859-1

-B&H-LucidaBright-Medium-R-Normal--11-80-100-100-P-63-ISO8859-1
-B&H-LucidaBright-Medium-R-Normal--14-100-100-100-P-80-ISO8859-1
-B&H-LucidaBright-Medium-R-Normal--17-120-100-100-P-96-ISO8859-1
-B&H-LucidaBright-Medium-R-Normal--20-140-100-100-P-114-ISO8859-1
-B&H-LucidaBright-Medium-R-Normal--25-180-100-100-P-142-ISO8859-1
-B&H-LucidaBright-Medium-R-Normal--26-190-100-100-P-149-ISO8859-1
-B&H-LucidaBright-Medium-R-Normal--34-240-100-100-P-193-ISO8859-1
-B&H-LucidaBright-Medium-I-Normal--11-80-100-100-P-63-ISO8859-1
-B&H-LucidaBright-Medium-I-Normal--14-100-100-100-P-80-ISO8859-1
-B&H-LucidaBright-Medium-I-Normal--17-120-100-100-P-96-ISO8859-1
-B&H-LucidaBright-Medium-I-Normal--20-140-100-100-P-113-ISO8859-1
-B&H-LucidaBright-Medium-I-Normal--25-180-100-100-P-142-ISO8859-1
-B&H-LucidaBright-Medium-I-Normal--26-190-100-100-P-148-ISO8859-1
-B&H-LucidaBright-Medium-I-Normal--34-240-100-100-P-194-ISO8859-1
-B&H-LucidaBright-DemiBold-R-Normal--11-80-100-100-P-66-ISO8859-1
-B&H-LucidaBright-DemiBold-R-Normal--14-100-100-100-P-84-ISO8859-1
-B&H-LucidaBright-DemiBold-R-Normal--17-120-100-100-P-101-ISO8859-1
-B&H-LucidaBright-DemiBold-R-Normal--20-140-100-100-P-118-ISO8859-1
-B&H-LucidaBright-DemiBold-R-Normal--25-180-100-100-P-149-ISO8859-1
-B&H-LucidaBright-DemiBold-R-Normal--26-190-100-100-P-155-ISO8859-1
-B&H-LucidaBright-DemiBold-R-Normal--34-240-100-100-P-202-ISO8859-1
-B&H-LucidaBright-DemiBold-I-Normal--11-80-100-100-P-66-ISO8859-1
-B&H-LucidaBright-DemiBold-I-Normal--14-100-100-100-P-84-ISO8859-1
-B&H-LucidaBright-DemiBold-I-Normal--17-120-100-100-P-101-ISO8859-1
-B&H-LucidaBright-DemiBold-I-Normal--20-140-100-100-P-119-ISO8859-1
-B&H-LucidaBright-DemiBold-I-Normal--25-180-100-100-P-149-ISO8859-1
-B&H-LucidaBright-DemiBold-I-Normal--26-190-100-100-P-156-ISO8859-1
-B&H-LucidaBright-DemiBold-I-Normal--34-240-100-100-P-203-ISO8859-1

-B&H-LucidaTypewriter-Medium-R-Normal-Sans-11-80-100-100-M-70-ISO8859-1
-B&H-LucidaTypewriter-Medium-R-Normal-Sans-14-100-100-100-M-80-ISO8859-1
-B&H-LucidaTypewriter-Medium-R-Normal-Sans-17-120-100-100-M-100-ISO8859-1
-B&H-LucidaTypewriter-Medium-R-Normal-Sans-20-140-100-100-M-120-ISO8859-1
-B&H-LucidaTypewriter-Medium-R-Normal-Sans-25-180-100-100-M-150-ISO8859-1
-B&H-LucidaTypewriter-Medium-R-Normal-Sans-26-190-100-100-M-159-ISO8859-1
-B&H-LucidaTypewriter-Medium-R-Normal-Sans-34-240-100-100-M-200-ISO8859-1
-B&H-LucidaTypewriter-Bold-R-Normal-Sans-11-80-100-100-M-70-ISO8859-1
-B&H-LucidaTypewriter-Bold-R-Normal-Sans-14-100-100-100-M-80-ISO8859-1
-B&H-LucidaTypewriter-Bold-R-Normal-Sans-17-120-100-100-M-100-ISO8859-1
-B&H-LucidaTypewriter-Bold-R-Normal-Sans-20-140-100-100-M-120-ISO8859-1
-B&H-LucidaTypewriter-Bold-R-Normal-Sans-25-180-100-100-M-150-ISO8859-1
-B&H-LucidaTypewriter-Bold-R-Normal-Sans-26-190-100-100-M-159-ISO8859-1
-B&H-LucidaTypewriter-Bold-R-Normal-Sans-34-240-100-100-M-200-ISO8859-1

--------------------------------------------------------------------
New Century Schoolbook

normal (R), italic (I), bold (B), bold italic (BI)

-Adobe-New Century Schoolbook-Medium-R-Normal--11-80-100-100-P-60-ISO8859-1
-Adobe-New Century Schoolbook-Medium-R-Normal--14-100-100-100-P-82-ISO8859-1
-Adobe-New Century Schoolbook-Medium-R-Normal--17-120-100-100-P-91-ISO8859-1
-Adobe-New Century Schoolbook-Medium-R-Normal--20-140-100-100-P-103-ISO8859-1
-Adobe-New Century Schoolbook-Medium-R-Normal--25-180-100-100-P-136-ISO8859-1
-Adobe-New Century Schoolbook-Medium-R-Normal--34-240-100-100-P-181-ISO8859-1
-Adobe-New Century Schoolbook-Medium-I-Normal--11-80-100-100-P-60-ISO8859-1
-Adobe-New Century Schoolbook-Medium-I-Normal--14-100-100-100-P-81-ISO8859-1
-Adobe-New Century Schoolbook-Medium-I-Normal--17-120-100-100-P-92-ISO8859-1
-Adobe-New Century Schoolbook-Medium-I-Normal--20-140-100-100-P-104-ISO8859-1
-Adobe-New Century Schoolbook-Medium-I-Normal--25-180-100-100-P-136-ISO8859-1
-Adobe-New Century Schoolbook-Medium-I-Normal--34-240-100-100-P-182-ISO8859-1
-Adobe-New Century Schoolbook-Bold-R-Normal--11-80-100-100-P-66-ISO8859-1
-Adobe-New Century Schoolbook-Bold-R-Normal--14-100-100-100-P-87-ISO8859-1
-Adobe-New Century Schoolbook-Bold-R-Normal--17-120-100-100-P-99-ISO8859-1
-Adobe-New Century Schoolbook-Bold-R-Normal--20-140-100-100-P-113-ISO8859-1
-Adobe-New Century Schoolbook-Bold-R-Normal--25-180-100-100-P-149-ISO8859-1
-Adobe-New Century Schoolbook-Bold-R-Normal--34-240-100-100-P-193-ISO8859-1
-Adobe-New Century Schoolbook-Bold-I-Normal--11-80-100-100-P-66-ISO8859-1
-Adobe-New Century Schoolbook-Bold-I-Normal--14-100-100-100-P-88-ISO8859-1
-Adobe-New Century Schoolbook-Bold-I-Normal--17-120-100-100-P-99-ISO8859-1
-Adobe-New Century Schoolbook-Bold-I-Normal--20-140-100-100-P-111-ISO8859-1
-Adobe-New Century Schoolbook-Bold-I-Normal--25-180-100-100-P-148-ISO8859-1
-Adobe-New Century Schoolbook-Bold-I-Normal--34-240-100-100-P-193-ISO8859-1

--------------------------------------------------------------------
Symbol

-Adobe-Symbol-Medium-R-Normal--11-80-100-100-P-61-ADOBE-FONTSPECIFIC
-Adobe-Symbol-Medium-R-Normal--14-100-100-100-P-85-ADOBE-FONTSPECIFIC
-Adobe-Symbol-Medium-R-Normal--17-120-100-100-P-95-ADOBE-FONTSPECIFIC
-Adobe-Symbol-Medium-R-Normal--20-140-100-100-P-107-ADOBE-FONTSPECIFIC
-Adobe-Symbol-Medium-R-Normal--25-180-100-100-P-142-ADOBE-FONTSPECIFIC
-Adobe-Symbol-Medium-R-Normal--34-240-100-100-P-191-ADOBE-FONTSPECIFIC

--------------------------------------------------------------------
Terminal

-Bitstream-Terminal-Medium-R-Normal--18-140-100-100-C-110-ISO8859-1
-Bitstream-Terminal-Bold-R-Normal--18-140-100-100-C-110-ISO8859-1

-Bitstream-Terminal-Medium-R-Normal--18-140-100-100-C-110-DEC-DECtech
-Bitstream-Terminal-Bold-R-Normal--18-140-100-100-C-110-DEC-DECtech

--------------------------------------------------------------------
Times

normal (R), italic (I), bold (B), bold italic (BI)

-Adobe-Times-Medium-R-Normal--11-80-100-100-P-54-ISO8859-1
-Adobe-Times-Medium-R-Normal--14-100-100-100-P-74-ISO8859-1
-Adobe-Times-Medium-R-Normal--17-120-100-100-P-84-ISO8859-1
-Adobe-Times-Medium-R-Normal--20-140-100-100-P-96-ISO8859-1
-Adobe-Times-Medium-R-Normal--25-180-100-100-P-125-ISO8859-1
-Adobe-Times-Medium-R-Normal--34-240-100-100-P-170-ISO8859-1
-Adobe-Times-Medium-I-Normal--11-80-100-100-P-52-ISO8859-1
-Adobe-Times-Medium-I-Normal--14-100-100-100-P-73-ISO8859-1
-Adobe-Times-Medium-I-Normal--17-120-100-100-P-84-ISO8859-1
-Adobe-Times-Medium-I-Normal--20-140-100-100-P-94-ISO8859-1
-Adobe-Times-Medium-I-Normal--25-180-100-100-P-125-ISO8859-1
-Adobe-Times-Medium-I-Normal--34-240-100-100-P-168-ISO8859-1
-Adobe-Times-Bold-R-Normal--11-80-100-100-P-57-ISO8859-1
-Adobe-Times-Bold-R-Normal--14-100-100-100-P-76-ISO8859-1
-Adobe-Times-Bold-R-Normal--17-120-100-100-P-88-ISO8859-1
-Adobe-Times-Bold-R-Normal--20-140-100-100-P-100-ISO8859-1
-Adobe-Times-Bold-R-Normal--25-180-100-100-P-132-ISO8859-1
-Adobe-Times-Bold-R-Normal--34-240-100-100-P-177-ISO8859-1
-Adobe-Times-Bold-I-Normal--11-80-100-100-P-57-ISO8859-1
-Adobe-Times-Bold-I-Normal--14-100-100-100-P-77-ISO8859-1
-Adobe-Times-Bold-I-Normal--17-120-100-100-P-86-ISO8859-1
-Adobe-Times-Bold-I-Normal--20-140-100-100-P-98-ISO8859-1
-Adobe-Times-Bold-I-Normal--25-180-100-100-P-128-ISO8859-1
-Adobe-Times-Bold-I-Normal--34-240-100-100-P-170-ISO8859-175-p-130-iso8859-1
```

I obviously haven't had time to try them all but so far this one is my favourite...

```
Eterm --geometry 100x75+50+40 --trans=true --borderless --scrollbar=true --buttonbar=false -f green --cmod 400 -c green --font-fx none --tint grey50 --font "-Adobe-Courier-Bold-R-Normal--14-100-100-100-M-90-ISO8859-1"
```

...and these are some other ones that I've tried, which seem to suit your criteria of bolder/larger/clearer...

```
Eterm --geometry 100x75+50+40 --trans=true --borderless --scrollbar=true --buttonbar=false -f green --cmod 400 -c green --font-fx none --tint grey50 --font "-Bitstream-Terminal-Medium-R-Normal--18-140-100-100-C-110-ISO8859-1"

Eterm --geometry 100x75+50+40 --trans=true --borderless --scrollbar=true --buttonbar=false -f green --cmod 400 -c green --font-fx none --tint grey50 --font "-B&H-LucidaTypewriter-Bold-R-Normal-Sans-14-100-100-100-M-80-ISO8859-1"

Eterm --geometry 100x75+50+40 --trans=true --borderless --scrollbar=true --buttonbar=false -f green --cmod 400 -c green --font-fx none --tint grey50 --font "-Adobe-Helvetica-Bold-R-Normal--17-120-100-100-P-92-ISO8859-1"

Eterm --geometry 100x75+50+40 --trans=true --borderless --scrollbar=true --buttonbar=false -f green --cmod 400 -c green --font-fx none --tint grey50 --font "-Adobe-Helvetica-Bold-R-Normal--14-100-100-100-P-82-ISO8859-1"
```

---

