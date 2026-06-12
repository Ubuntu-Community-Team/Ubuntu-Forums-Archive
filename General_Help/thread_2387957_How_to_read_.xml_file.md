---
title: "How to read .xml file"
date: 2018-03-26
forum: General Help
---

### Post by satimis on 2018-03-26
Hi all,

Please advise how to read .xml file?

&#10219; sed -n '/LANGUAGE/{N; s/.*<string>\(.*\)<\/string>.*/\1/p; }' smil.xml
No output

&#10219; apt-cache policy xmlcopyeditor```

xmlcopyeditor:
  Installed: (none)
  Candidate: 1.2.1.3-1build1
  Version table:
     1.2.1.3-1build1 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages

```

&#10219; apt-cache policy kxmleditor
N: Unable to locate package kxmleditor


Thanks

Regards
satimis

---

### Post by #&amp;thj^% on 2018-03-26
I know I'm going to regret this but your information given is a bit vague...any text editor wil open xml's files.

Now Ubuntu has a very good utility called "xmlto" that could help you. It converts xml to a variety of formats,** including plain text**, epub, pdf.
From:  xmlto --help
```

usage: xmlto [OPTION]... FORMAT XML
OPTIONs are:
  -v              verbose output (-vv for very verbose)
  -x stylesheet   use the specified stylesheet instead of choosing one
  -m fragment     use the XSL fragment to customize the stylesheet
  -o directory    put output in the specified directory instead of
                  the current working directory
  -p postprocopts pass option to postprocessor
  --extensions    turn on stylesheet extensions for this tool chain
  --noautosize    do not autodetect paper size via locales or paperconf
  --noclean       temp files are not deleted automatically
                  (good for diagnostics)
  --noextensions  do not use passivetex/fop extensions
  --profile       use profiling stylesheet
  --searchpath    colon-separated list of fallback directories
  --skip-validation
                  do not attempt to validate the input before processing
  --stringparam paramname=paramvalue
                  pass a named parameter to the stylesheet from the
                  command line
  --with-fop      use fop for formatting (if fop available)
  --with-dblatex  use dblatex for formatting (if dblatex available)

Available FORMATs depend on the type of the XML file (which is
determined automatically).

For documents of type "fo":
awt  dvi  mif  pcl  pdf  ps  svg  txt

For documents of type "xhtml1":
awt  dvi  fo  mif  pcl	pdf  ps  svg  txt

For documents of type "docbook":
awt  epub  html      html-nochunks  man  pcl  ps   txt	  xhtml-nochunks
dvi  fo    htmlhelp  javahelp	    mif  pdf  svg  xhtml

```

---

### Post by dragonfly41 on 2018-03-26
**XML Copy Edito**r is in Software Centre.

Name for installation through Synaptic: xmlcopyeditor

---

