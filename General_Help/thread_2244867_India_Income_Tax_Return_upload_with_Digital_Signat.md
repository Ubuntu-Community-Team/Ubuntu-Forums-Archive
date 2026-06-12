---
title: "India Income Tax Return upload with Digital Signatures"
date: 2014-09-19
forum: General Help
---

### Post by kagashe on 2014-09-19
I am using Ubuntu since version 5.04 and Windows only for submitting my Income Tax Return. The India Income Tax Return efiling site provides an Excel File Utility with Visual Basic Macro which could be run only on Windows to enter the data and convert into xml file for uploading to the site. Since this year the site is also providing Java utility which could be used on Linux as well. But one problem remains due to which I had to use Windows.

For Signing with Digital Signature there is a Javascript which requires JRE 7. The script works on Windows as well as Linux but it searches the .pfx file containing the Digital Signature on your machine in C:/fakepath Folder. Since there is no C:/ drive on Linux the script gives an error. On Windows you need to create a Folder fakepath on C:/ drive and keep the file in it. If you do not want to create the Foler fakepath there is following workaround for Internet Explorer:

In Tools/Internet_Options/Security/Custom find "include local directory path when uploading files to the server" and enable it.

I could not find any option to enable this feature in Firefox on Ubuntu.

Is it possible to enable this feature on Firefox?

Kamalakar

---

### Post by Frogs Hair on 2014-09-20
Support Question , ***&#8203;Moved to General Help***

---

### Post by kagashe on 2014-10-01
I am using Fogger for creating Web Application. I made one for Income Tax India Website and when I try to sign the error produced is following:
Can not read the file for signing C:\fakepath\filename.xml

In Fogger there is a provision to introduce Javascript in the Web Application through:
Fogger_Preferences/Customization/User_Scripts

where I can put a Javascript.

I googled for the solution and [got this]("http://stackoverflow.com/questions/21426232/how-to-remove-c-fakepath-in-webkit-browser-like-chrome-safari-opera").

Could someone help me how to write a Javascript and put in the Web Applications so that the browser does not look for C:\ drive for fakepath folder on Ubuntu.

Kamalakar

---

