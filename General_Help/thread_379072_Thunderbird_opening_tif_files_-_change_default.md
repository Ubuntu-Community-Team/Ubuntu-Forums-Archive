---
title: "Thunderbird opening tif files - change default"
date: 2007-03-08
forum: General Help
---

### Post by andrewsawyer on 2007-03-08
Hi All,

I hope this is a simple one, however it has me stumped.  I use Thunderbird for email as Evolution was chewing resources.  I have a fax to email service that sends through faxes as tif files.

My problem is that when opening the tif file in anything other than Evince, it comes through looking like it's been squashed.  Loading it with evince and it comes through fine, and I can see all pages of the fax if more than one.

Unfortunately Thunderbird always defaults to eog to open the attachments, and I have to choose other and then navigate to /usr/bin/evince to open them (or save to disk and open from the desktop where evince is set as the default program).

Is there a way to set evince in Thuderbird as the default program to open this file type?  Getting many faxes per day (this is a work laptop), I am wasting a lot of time navigating through directories each time I want to read a fax.

Your help would be appreciated!

Andy

---

### Post by pandu.rs on 2007-03-08
Edit->Preferences->Attachments->View & Edit Actions

---

### Post by andrewsawyer on 2007-03-08
Thank you,

unfortunately this is blank :-(

I've done some searching, and all I can find it to delete the mimeTypes.rdf file and restart Thuderbird (to create a new one).  This doesn't work - it just does the same again.

Any suggestions?  I don't feel comfortable editing the file manually, however all I'm trying to do it link extensions .tif with /usr/bin/evince.

Help would be greatly appreciated.

oh, my file is as follows:

```
<?xml version="1.0"?>  

<!--
 This file is used as a persistent data store for helper application
 information.

 The root of the data is the <RDF:Seq about="urn:mimetypes:root"/>. This
 contains one <RDF:li/> entry per MIME type.  Each <RDF:li/> entry corresponds
 to the "urn:mimetype:major/minor" resource, where "major/minor" is the MIME
 type.  For example, for HTML we would have "urn:mimetype:text/html".
 Typically, this resource will be in the <RDF:Description/> node which has the
 corresponding "about" attribute.

 Each "urn:mimetype:major/minor" resource can have the following properties:

   NC:Value - the MIME type string
   NC:editable - a "true" or "false" depending on whether this entry is
                 editable
   NC:description - a description of the type ("HTML Document" for text/html)
   NC:fileExtensions - there will be one of these properties per extension that
                       corresponds to this MIME type, each one having a single
                       extension as its value.
   NC:handlerProp - the way the type should be handled.  This corresponds to a
                    "urn:mimetype:handler:major/minor" resource.  Eg, the way
                    HTML is handled would be stored in the
                    "urn:mimetype:handler:text/html" resource

 Each "urn:mimetype:handler:major/minor" resource can have the following
 properties:

   NC:useSystemDefault - "true" if we should handle per default OS setting,
                          "false" or not set otherwise
   NC:saveToDisk - "true" if the data should be saved to disk, "false" or not
                   set otherwise.
     (Note - if both of these are false, that means "open in helper app")
   NC:alwaysAsk - "true" if the user should always be prompted before handling
                  data of this type, false otherwise.
   NC:externalApplication - the helper application to use for this type.  This
                            corresponds to a
                            "urn:mimetype:externalApplication:major/minor"
			    resource

 Each "urn:mimetype:externalApplication:major/minor" resource can have the
 following properties:

   NC:path - the path to the application
   NC:prettyName - the "pretty name" of the application ("Acrobat Reader" for
                   /usr/bin/acroread, eg).
-->
			
<RDF:RDF xmlns:RDF="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
         xmlns:NC="http://home.netscape.com/NC-rdf#">

  <RDF:Description about="urn:mimetypes"> 
    <NC:MIME-types> 
      <RDF:Seq about="urn:mimetypes:root"> 
      </RDF:Seq>
    </NC:MIME-types> 
  </RDF:Description> 
</RDF:RDF>
```

---

### Post by pandu.rs on 2007-03-08
I came across this extension which may help you,

[https://nic-nac-project.org/~kaosmos/index-en.html#openattach](https://nic-nac-project.org/~kaosmos/index-en.html#openattach)

---

### Post by andrewsawyer on 2007-03-08
you're a star.

Thank you for your help.  This fixed it.

---

