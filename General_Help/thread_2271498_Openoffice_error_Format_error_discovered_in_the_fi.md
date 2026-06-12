---
title: "Openoffice error: Format error discovered in the file in sub-document content.xml"
date: 2015-03-30
forum: General Help
---

### Post by alicia5 on 2015-03-30
Hello to everybody!!

This is my first post. So, thanks a lot in advance for your help and I apologise for my english in case is not adequate.

I'm facing a huge problem, at least from my point of view. I was finishing a huge research (that I should deliver tomorrow first thing). I saved it in my computer and I went out to the supermarket. When I came back and tried to restart with the .ods file, the file was corrupted. I have a copy of the file but it is corrupted too. Both are the only files that cannot be openned in my computer, nor with the other computer I have at home (and works with Windows - Microsoft Office 2010).

The problem shown is the following one: 
Read-Error.
Format error discovered in the file in sub-document content.xml at 2,30819(row,col).

I've been looking for solving it reading some forums, switching to .zip and unzipping it, but I have no idea how to solve the problem with the content .xml. I don't know how to find the error and solve it. Would it be possible to be helped, please?

I've attached the file, just in case someone could have a look at it.

I look forward to hear from you and once more, great and more great thanks.

All the best,

Alicia

---

### Post by Holger_Gehrke on 2015-03-30
Here you go. Opens fine in oocalc 3 after I unzipped,ran xmllint, fixed the errors in an editor and zipped it again.

---

### Post by alicia5 on 2015-03-30
Wow!!!!!! It runs!!!!

Really thanks for your help!! It is really much appreciated!!

Best wishes!

Alicia

---

### Post by abe7 on 2015-06-11
Hey,

I'm having the exact same problem with my manuscript that I've been working forever on. I'm seriously at a loss at how to fix this, and if you could help me out I wouldn't even know what to say...

Here's the file in questions. It's ODT

---

### Post by Bucky Ball on 2015-06-11
> **abe7 said:**
> Hey,

I'm having the exact same problem with my manuscript that I've been working forever on. I'm seriously at a loss at how to fix this, and if you could help me out I wouldn't even know what to say...

Here's the file in questions. It's ODT

The answer has been provided.

> **Holger_Gehrke said:**
> Here you go. Opens fine in oocalc 3 after I unzipped,ran xmllint, fixed the errors in an editor and zipped it again.

Try this and if you have any questions about how to, ask.

@alicia5: Please mark the thread as solved by checking the second link in my signature. Thanks. :)

---

### Post by abe7 on 2015-06-11
Hey Bucky,

I appreciate the response!

I guess I didn't clarify enough, my fault. I saw the solution, however (due to my limited knowledge) it doesn't make a whole lot of sense to me.

Meaning, I don't know how to go about doing that for myself.

---

### Post by Holger_Gehrke on 2015-06-11
> **abe7 said:**
> 
I guess I didn't clarify enough, my fault. I saw the solution, however (due to my limited knowledge) it doesn't make a whole lot of sense to me.

Meaning, I don't know how to go about doing that for myself.

To clarify the explanation I gave to alicia5: all Open/Libre Office files are actually zip-files full of XML-files for content and formatting with some other files for images and the like. So just unzip your file into a new directory. Then run xmllint from the package libxml2-utils on the command line and pass it the name of the file as a parameter ('xmllint content.xml'). The output of this will tell you what's wrong with the file (in your case the attribute 'office:name' is defined multiple times for a style for an annotation). Now comes the ... interesting ... part. Open 'content.xml' in your editor of choice and find the problematic element. It should be an editor that has no problem with working on a file which has several hundred kilobyte of text (about 700 kb in you case) all on one line. I personally use emacs, but your mileage may vary ... severely. Just erase the first four definition of "office:name" from the definition, save, exit, zip everything back together and rename the new zip-file to whatever-you-want.odt. Done.

And to save you the trouble, here's your fixed file.

---

### Post by abe7 on 2015-06-11
Oh my goodness. Thank you SO incredibly much Holger!

You have no idea how much time you just saved me/how much this means to me :)

Also thank you so much for the explanation, however I've learned through this mess to auto backup my files so I never have to have this issue again.

Take care!
Abe

---

### Post by warren_ on 2015-11-27
Hi Folks, 

I am in the same boat as the previous hapless individuals in this thread. The problem is that I could be standing on a stepladder and still have the proffered "solution" sail right over my head. 

In my case the specifics of the error (on the off chance that it helps) are as follows:

[B]Read-Error.
Format error discovered in the file in sub-document content.xml at 2,3669(row,col).

[/B]File attached. If any kindly ubuntu god or goddess could have a look and work their divine juju on it, I'd be grateful

&#8212;&#8212;&#8212;

Update: Well, I have managed to work through **some** of the solution myself (desperation is an amazing teacher). I have extracted the content.xml, and looking at it with a text editor, it looks like there is a problem with office:name attribution (??), _but I have not been able to download/run xmllint and can't figure out how to fix the content.xml file._

I'd attach the xml file but it doesn't look like the forum will accept xml attachments.

&#8212;&#8212;&#8212;

Update: Solved. Eventually managed to find someone savvier than me (not that hard really) and got it fixed. Great info in this thread though. Thanks to Holger especially.

---

### Post by Bucky Ball on 2015-11-27
If you could perhaps just share how you fixed it on the forums instead of posting a document (which won't open for me). Thanks.

---

### Post by bluejay88 on 2016-01-18
I too have this same problem with my ODT file. When opening document I get: 
Read-Error. 
Format error discovered in the file in sub-document content.xml at 2, 2915 (row, col)

I was able to unzip the file, open the content.xml file in an editor app, but have no idea how to fix the problem, which again, looks similar to others in this thread regarding the name attribute being the same.  
would greatly appreciate it if someone can please figure this out for me. I'm a newbie at all this. Thanks!

---

### Post by Holger_Gehrke on 2016-01-19
> **bluejay88 said:**
> I too have this same problem with my ODT file. When opening document I get: 
Read-Error. 
Format error discovered in the file in sub-document content.xml at 2, 2915 (row, col)


The message means: the error is on the second line (not really surprising; **all** content is on the second line of the xml-file - which makes it one *seriously* long line ...) at the 2915th character.

The reason I use emacs for fixing this problem is the nXML-mode of emacs, which does syntax-highlighting on XML and marks errors in an eye-catching [COLOR=#ff0000]RED[/COLOR]. 

The error was the same problem as in the previous cases, the same attribute defined multiple times in the same tag:
```

<style:style 
office:name="__Annotation__75_755257625111111111111111111111111111111111111111111" 
[COLOR=#ff0000]office:name[/COLOR]="__Annotation__80_755257625111111111111111111111111111111111111111111" 
[COLOR=#ff0000]office:name[/COLOR]="__Annotation__92_75525762511111111111111111111111111111111" 
[COLOR=#ff0000]office:name[/COLOR]="__Annotation__108_7552576251111111111111111111111111111111111"
[COLOR=#ff0000]office:name[/COLOR]="__Annotation__124_75525762511111111111111111111111111" 
[COLOR=#ff0000]office:name[/COLOR]="__Annotation__176_75525762511111" 
style:name="P1" style:family="paragraph" style:parent-style-name="Standard">

```

Removing the 5 extraneous "office:name" attributes fixes the file.

---

### Post by bluejay88 on 2016-01-19
Holger you are a GOD!!! Thank you so very much!!!

---

### Post by Bucky Ball on 2016-01-19
Excellent news. Please see the first link in my signature and share with us how you fixed. Thanks.

---

