---
title: "Help with VB6..."
date: 2007-10-06
forum: General Help
---

### Post by Ninjah on 2007-10-06
Hello Everyone,

  Well.. im kind of new to the whole programming scene & my brother in-law introduced me to VB6, so ive been playing around with it for a few days, learning a few things here and there... I came across a little problem that im not sure how to fix, there has to be a way but i cant seem to find an easier code... 
for example i have 36 pictures to change within a form with 1 button for each picture... so my problem is the way im doing the code it seems to lag because its tooooo big... is there an easier way?

My Code example..
====================================================
Private Sub Command1_Click()
Image1.Visible = True
Image2.Visible = False
Image3.Visible = False
Image4.Visible = False
Image5.Visible = False
Image6.Visible = False
Image7.Visible = False
Image8.Visible = False
Image9.Visible = False
Image10.Visible = False
Image11.Visible = False
Image12.Visible = False
Image13.Visible = False
Image14.Visible = False
Image15.Visible = False
Image16.Visible = False
Image17.Visible = False
Image18.Visible = False
Image19.Visible = False
Image20.Visible = False
Image21.Visible = False
Image22.Visible = False
Image23.Visible = False
Image24.Visible = False
Image25.Visible = False
Image26.Visible = False
Image27.Visible = False
Image28.Visible = False
Image29.Visible = False
Image30.Visible = False
Image31.Visible = False
Image32.Visible = False
Image33.Visible = False
Image34.Visible = False
Image35.Visible = False
Image36.Visible = False
End Sub
====================================================

Is there a way to do: 

If image1.visible = True Then
image2.visible through image36.visible = false

   (Or something like this)


Because i have that 36 times on my Code, for each of the buttons that i want to show a different picture for... O.o i know its probably something newbish, but thats as much as i know how to do... sorry if its a dumb question, thanks in advance for anyone who can help....

---

### Post by xuheir on 2008-05-02
First I would create an Image array;
so you will have Image(1), Image(2) ... Image(36)
and a Button array
Command(1) to Command(36)


then:

dim i as integer

Private sub Command1_Click(index as integer)

'hide all images
for i = 1 to 36
  Image(i).Visible = False
next i

'show the image corresponds to the command button No
image(index).visible

end sub

hope this will help... I typed the code here without checking from the ide I don't have VB installed on this box

---

