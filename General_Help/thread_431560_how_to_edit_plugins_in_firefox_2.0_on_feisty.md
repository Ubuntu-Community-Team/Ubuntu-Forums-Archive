---
title: "how to edit plugins in firefox 2.0 on feisty?"
date: 2007-05-03
forum: General Help
---

### Post by sveinn on 2007-05-03
Hello, 

I'm trying to change default plugins for firefox 2.0 on Feisty. 

(To have Helix play Real Networks mime types, for example, instead of Mplayer.)

Can't find a place to do so in the Firefox menu.

Looked at mimeTypes.rdf but it looks like:

<?xml version="1.0"?>  

<RDF xmlns="http://www.w3.org/1999/02/22-rdf-syntax-ns#" xmlns:NC="http://home.netscape.com/NC-rdf#">

  <Description about="urn:mimetypes"> 
    <NC:MIME-types> 
	    <Seq about="urn:mimetypes:root"> 
	    </Seq> 
    </NC:MIME-types> 
  </Description> 
</RDF>

So it's not obvious how to edit it.

Any clues?

Sveinn

---

### Post by orb9220 on 2007-05-03
I think I saw a extension at firefox site that allows you to configure mime types.

---

