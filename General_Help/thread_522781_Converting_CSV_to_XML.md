---
title: "Converting CSV to XML"
date: 2007-08-11
forum: General Help
---

### Post by Cornbreadly on 2007-08-11
I am not a programmer.

I am trying to cut and paste together  a custom Google Map with about 1500+ markers.  The CSV spreadsheet I have cannot be converted into XML markup with my current knowledge level and tools. The tutorial I found and will be using parses an XML that stores all of the data.   I understand that this is not a linux question or problem, but I am looking for linux solution.  

Everything I have found previously doesn't seem to work...
-xml2 is a filter that is not command line based.  I don't know where to begin to implement that one.
-ffe is command line based and i have not found a tutorial specific enough to help
-Gnumeric saves in a native xml format but the mark-up is all wrong
-OO spreadsheet exports into extra formats but not xml directly
-some code snippets are out there but I do not know how to use them

A simple xml var system assigned to the header row would work great

Pointers or advice would be very welcome

---

### Post by mdebusk on 2007-08-11
> **Cornbreadly said:**
> 
Pointers or advice would be very welcome


You'll probably need to post two things: a sample line or two from the CSV file, and an example of what you want the XML to look like.

I've done this in Rexx. I haven't yet learned how to work in any of the more-popular-on-Linux languages. (It's a shame Rexx isn't more widely used on Linux.)

---

### Post by kostkon on 2007-08-11
As I understand it, you want to do a one-off conversion of a CSV file to a specific XML format, right?

Since you are not a programmer an easy solution for you would be XSLT. You will only need to learn some XSLT by following a tutorial from the net. XSLT, being itself a XML dialect, allows you to transform one XML dialect to another one.

It's markup language you will need to learn, you will not need to learn anything about programming. Also, on the net you will find ready XSLT stylesheet files that will allow you to do the trasformation from CSV to XML without the need for you to make one stylesheet from the beginning, [like this one here]("http://ajwelch.blogspot.com/2007/02/csv-to-xml-converter-in-xslt-20.html").

The only thing you would need to do is to adapt it to the XML format you want to use. And that's why I'm saying that you will need to learn XSLT a little.

Then you will have to find a XML editor application that supports transformations with XSLT stylesheets. You can pick up XML editor from **Add/Remove** and see if they support this feature. At the moment, I cannot recommend you a specific application that supports this for sure.

---

### Post by Cornbreadly on 2007-08-11
Ok, I think we are on the right track.  It looks like I already have a tool to use the style sheet, xsltproc.

From my understanding, that tool mentioned above would load the parameters that Kostkon referred me to, then I would input the csv file and get the XML mark-up as the output.

The walk through I found is a little [over my head]("http://xmlsoft.org/XSLT/tutorial/libxslttutorial.html").

The author is referring to terms and functions generally for example, passing the integer value "1" to "xmlSubstituteEntitiesDefault."

I just do not know where to start.

I appreciate the help thus far.

---

### Post by Cornbreadly on 2007-08-12
Any other advice?  Any map makers out there who have a better way to plot 1500+ markers with specific info relating to each one?

Maybe a better way to have the map API draw from a soruce than xml or a conveinent way to make an xml than converting from a CSV file?

I am open to any ideas.

---

### Post by Cornbreadly on 2007-08-12
Invoke Linux Power!!!!

---

