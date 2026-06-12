---
title: "Convert problems"
date: 2020-12-17
forum: General Help
---

### Post by rudolf-kunzli on 2020-12-17
Hello all

I am trying to convert a png file to pdf.
The message below shows up
---
 convert florige_rk.pdf x.png
convert-im6.q16: attempt to perform an operation not allowed by the security policy `PDF' @ error/constitute.c/IsCoderAuthorized/408.
convert-im6.q16: no images defined `x.png' @ error/convert.c/ConvertImageCommand/3258.
---
The very same happens when I try to convert pdf into a png or jpg...
As long no pdf is involved everything runs fine.
It looks as only pdf files give me the troubles...

Any help/idea ?
Thanks

---

### Post by #&amp;thj^% on 2020-12-17
Look carefully.
```

convert xyz.png xyz.pdf ###should do the trick.
```

See man convert for more options. it requires the "ImageMagick" package.

I'll add with a caution additionally you can use wildcards: convert *.png file.pdf

---

### Post by rudolf-kunzli on 2020-12-17
I just use:
**convert florige_rk.pdf x.png  (mentionned in my message)**
and this provides the error.
I'll check for imagemagick then.
Anyway I can't understand why it works for conversion except when a pdf is involved...

---

### Post by rudolf-kunzli on 2020-12-17
ImageMagick is installed already...

---

### Post by #&amp;thj^% on 2020-12-17
Never mind I skimmed over the important part "attempt to perform an operation not allowed by the security policy `PDF' @ error/constitute.c/IsCoderAuthorized/408."
Lets have a look at:
Mine will look different than yours I've already edited it.
```
cat /etc/ImageMagick-6/policy.xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policymap [
  <!ELEMENT policymap (policy)+>
  <!ATTLIST policymap xmlns CDATA #FIXED ''>
  <!ELEMENT policy EMPTY>
  <!ATTLIST policy xmlns CDATA #FIXED '' domain NMTOKEN #REQUIRED
    name NMTOKEN #IMPLIED pattern CDATA #IMPLIED rights NMTOKEN #IMPLIED
    stealth NMTOKEN #IMPLIED value CDATA #IMPLIED>
]>
<!--
  Configure ImageMagick policies.

  Domains include system, delegate, coder, filter, path, or resource.

  Rights include none, read, write, execute and all.  Use | to combine them,
  for example: "read | write" to permit read from, or write to, a path.

  Use a glob expression as a pattern.

  Suppose we do not want users to process MPEG video images:

    <policy domain="delegate" rights="none" pattern="mpeg:decode" />

  Here we do not want users reading images from HTTP:

    <policy domain="coder" rights="read | write" pattern="PDF" />

  The /repository file system is restricted to read only.  We use a glob
  expression to match all paths that start with /repository:

    <policy domain="path" rights="read" pattern="/repository/*" />

  Lets prevent users from executing any image filters:

    <policy domain="filter" rights="none" pattern="*" />

  Any large image is cached to disk rather than memory:

    <policy domain="resource" name="area" value="1GP"/>

  Define arguments for the memory, map, area, width, height and disk resources
  with SI prefixes (.e.g 100MB).  In addition, resource policies are maximums
  for each instance of ImageMagick (e.g. policy memory limit 1GB, -limit 2GB
  exceeds policy maximum so memory limit is 1GB).

  Rules are processed in order.  Here we want to restrict ImageMagick to only
  read or write a small subset of proven web-safe image types:

    <policy domain="delegate" rights="none" pattern="*" />
    <policy domain="filter" rights="none" pattern="*" />
    <policy domain="coder" rights="none" pattern="*" />
    <policy domain="coder" rights="read|write" pattern="{GIF,JPEG,PNG,WEBP}" />
-->
<policymap>
  <!-- <policy domain="system" name="shred" value="2"/> -->
  <!-- <policy domain="system" name="precision" value="6"/> -->
  <!-- <policy domain="system" name="memory-map" value="anonymous"/> -->
  <!-- <policy domain="system" name="max-memory-request" value="256MiB"/> -->
  <!-- <policy domain="resource" name="temporary-path" value="/tmp"/> -->
  <policy domain="resource" name="memory" value="256MiB"/>
  <policy domain="resource" name="map" value="512MiB"/>
  <policy domain="resource" name="width" value="16KP"/>
  <policy domain="resource" name="height" value="16KP"/>
  <!-- <policy domain="resource" name="list-length" value="128"/> -->
  <policy domain="resource" name="area" value="128MB"/>
  <policy domain="resource" name="disk" value="1GiB"/>
  <!-- <policy domain="resource" name="file" value="768"/> -->
  <!-- <policy domain="resource" name="thread" value="4"/> -->
  <!-- <policy domain="resource" name="throttle" value="0"/> -->
  <!-- <policy domain="resource" name="time" value="3600"/> -->
  <!-- <policy domain="coder" rights="none" pattern="MVG" /> -->
  <!-- <policy domain="module" rights="none" pattern="{PS,PDF,XPS}" /> -->
  <!-- <policy domain="delegate" rights="none" pattern="HTTPS" /> -->
  <!-- <policy domain="path" rights="none" pattern="@*" /> -->
  <!-- <policy domain="cache" name="memory-map" value="anonymous"/> -->
  <!-- <policy domain="cache" name="synchronize" value="True"/> -->
  <!-- <policy domain="cache" name="shared-secret" value="passphrase" stealth="true"/> -->
  <!-- <policy domain="system" name="pixel-cache-memory" value="anonymous"/> -->
  <!-- <policy domain="system" name="shred" value="2"/> -->
  <!-- <policy domain="system" name="precision" value="6"/> -->
  <!-- not needed due to the need to use explicitly by mvg: -->
  <!-- <policy domain="delegate" rights="none" pattern="MVG" /> -->
  <!-- use curl -->
  <policy domain="delegate" rights="none" pattern="URL" />
  <policy domain="delegate" rights="none" pattern="HTTPS" />
  <policy domain="delegate" rights="none" pattern="HTTP" />
  <!-- in order to avoid to get image with password text -->
  <policy domain="path" rights="none" pattern="@*"/>
  <!-- disable ghostscript format types -->
  <policy domain="coder" rights="none" pattern="PS" />
  <policy domain="coder" rights="none" pattern="PS2" />
  <policy domain="coder" rights="none" pattern="PS3" />
  <policy domain="coder" rights="none" pattern="EPS" />
  <policy domain="coder" rights="none" pattern="PDF" />
  <policy domain="coder" rights="none" pattern="XPS" />
</policymap>
 
```
Due to a security flaw in Ghostscript. 
amend the line:
```
<policy domain="coder" rights="read | write" pattern="PDF" />
```
**EDIT:** Did you also know you can save any .jpg .png yada yada as a PDF with your imageviewer?
The security vulnerability that caused distributions to implement the policy is referenced here: [https://www.kb.cert.org/vuls/id/332928/](https://www.kb.cert.org/vuls/id/332928/)

---

### Post by andrew.46 on 2020-12-18
Some discussion on this issue [here...]("https://askubuntu.com/a/1181773/57576")

---

### Post by rudolf-kunzli on 2020-12-18
Thanks a lot.
I added that line and it works fine now.
I just wonder how that happened to a new install...
All other systems (not installed recently) don't seem to have the same problem.

---

