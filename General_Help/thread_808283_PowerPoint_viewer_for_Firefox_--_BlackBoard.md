---
title: "PowerPoint viewer for Firefox -- BlackBoard"
date: 2008-05-26
forum: General Help
---

### Post by pbewig on 2008-05-26
I am running Hardy Heron with all current upgrades on an AMD-64 homebuilt, and using the Firefox browswer.

My daughter is taking a telecourse from the local community college using BlackBoard.  The instructor posted a PowerPoint presentation that the students must read.  Firefox loads the presentation, but it is garbled and unreadable.

What must I do to be able to read this PowerPoint presentation?

---

### Post by Gunman1982 on 2008-05-26
Those webpages created by Powerpoint are sadly optimized to run with an InternetExplorer. You could try to install wine and use the IE trough that. Or hit the instructor for using such software.

---

### Post by dasunst3r on 2008-05-26
If it is an option, she could also download the .ppt file straight from Blackboard and read it using OpenOffice.

---

### Post by pbewig on 2008-05-26
The link doesn't go to a .ppt file.  I don't know if the instructor used PowerPoint to save in some "web-friendly" format (that bundles in something Firefox can't read) or if BlackBoard wraps it somehow.

I tried downloading the file that the link points to, and Open Office can open it, but it just has a redirect message -- the redirect message doesn't say what link it is redirecting to, and the link is lost when Open Office opens the page.

I refuse to install Internet Explorer.  And it probably wouldn't help, anyway, since I imagine Internet Explorer calls something else to view the PowerPoint content.

---

### Post by dasunst3r on 2008-05-26
There's always the route of asking the professor to post the .ppt file to Course Documents.  My professors have been very accommodating in terms of this, and I hope that your daughter's professors are too.  Just remember: be polite. :)

---

### Post by pbewig on 2008-05-26
The instructor will not change the file format to accommodate my daughter, suggesting instead that she use one of the computer labs on campus.  She does not seem to see the irony in suggesting that a student taking a remote course should come to campus in order to take the course.

---

### Post by wootah on 2008-05-26
I hate blackboard. Even since they bought WebCT, that product has gone down hill, imo. You should hear the students and faculty complain about it at my university :) 

Anyways, as dasunst3r suggested, it would probably be best to download the .ppt file and use OpenOffice to view it.

EDIT: Well I guess they use a wrapper then. Let me see what I can do--I'll check one of my courses and see if there is a way around it.

---

### Post by wootah on 2008-05-26
When I try and view a .ppt through BlackBoard, I get the option to download the file. I am using Firefox 2 on a Windows machine, however.

---

### Post by pbewig on 2008-05-26
I also hate BlackBoard.  I agree it has gone downhill in recent years, since the acquisition of WebCT and since they were awarded their patent and sued Desire To Learn.  And I don't think it was very far uphill before that.

I'm not sure where the formatting problem comes from.  I suspect PowerPoint rather than BlackBoard.  I think the Office 2007 version of PowerPoint has a way to save a presentation in a "web-enhanced" format that mixes some html, some javascript, and some IE-only extensions.  If it was just a PowerPoint file then Open Office could read it.  But it's not a .ppt file.

---

### Post by Gunman1982 on 2008-05-26
Well as far as I know is that the Powerpoint charts landing in Blackboard are html pages with some microsoft code which works fine in Internet Explorer (under most circumstances since those Microsoft bastards have now a big problem to offer backward compability with their own **** and still support new web standards). This code however isn't handled well by firefox/opera/safari. So no the Internet Explorer doesn't call to Powerpoint functionality since if you don't have it installed you wouldn't be able to see those pages.

---

### Post by pbewig on 2008-05-26
The type of the file is an .htm file.  I'll look at the page source and see if I can find the underlying .ppt file.

---

### Post by wootah on 2008-05-26
> **Gunman1982 said:**
> Well as far as I know is that the Powerpoint charts landing in Blackboard are html pages with some microsoft code which works fine in Internet Explorer (under most circumstances since those Microsoft bastards have now a big problem to offer backward compability with their own **** and still support new web standards). This code however isn't handled well by firefox/opera/safari. So no the Internet Explorer doesn't call to Powerpoint functionality since if you don't have it installed you wouldn't be able to see those pages.

Arg! This is the typical MS behavior that pisses me right off and has led me to leave Windows, Microsoft and their proprietary strong arming. At my university, I have refused a lot of crap sent to me as .doc and I have asked them to resend as .pdf or .odt.

Perhaps another polite attempt explaining your circumstance (ie, it's an open learning course and you don't have access to get to the campus) will help you get the original ppt.

If I may ask, what college/university is offering the remote service?

---

### Post by pbewig on 2008-05-26
I looked at the page source.  It contains a javascript function that ensures the browser is properly supported (the test is MSIE >= 4.0 and not Mac) and, if it is, calls:

document.writeln('<div style="visibility:hidden">');
document.writeln('</div>');

---

### Post by pbewig on 2008-05-26
I've continued looking at the page source.  I am not expert in html or javascript, but I see a reference to a page

Intelligence%20and%20Creativity_files/frame.htm

which seems to contain the content.  But when I load that page directly, it's just blank.

---

### Post by pbewig on 2008-05-26
Unless anybody has any other ideas, I'm ready to declare failure.  My daughter does have ready access to the campus (she is taking another course that meets on campus, and the campus is only about fifteen minutes from home); she is taking this telecourse only because that is how the course is offered.  And she can also see the course materials if she goes to our local library.

I will ask my daughter to explain again to the instructor why she is having problems reading the course content and ask that the original .ppt file be made available.

Thanks to all,

Phil

---

