---
title: "How to create your own attractive boot screen art"
date: 2006-07-01
forum: General Help
---

### Post by Kensey on 2006-07-01
When it comes to customizing your boot progress usplash, all art is not created equal.  Here are some guidelines for choosing (or creating) good usplash art.

**[SIZE="3"]Visual appearance[/SIZE]**

[LIST]
[*] Try to pick art that has a definite background color that extends to its borders, then use that color as palette entry 0.  Otherwise, you end up with an inset effect -- either the edges of the cut-off object(s) in the image reveal the edges, or the background color itself does if you don't set it properly in the palette.

[*] Use art with some "dead space" -- 80 pixels total at top and bottom (all one side or the other is fine, or split in any proportion, as long as there are 80 pixels of empty vertical space).  This lets you (or someone else) trim a 640x480 version to 640x400 for use with the default VGA framebuffer mode.  Also try to make sure the lower half of the image is relatively empty or doesn't have anything too important in it -- that's where your progress bar and boot messages will display, so anything there is basically going to be invisible anyway.

[*] Pick art that isn't "busy" with lots of subtle gradients and shading, and if possible try to use something that has a dominant color -- otherwise the conversion to 16 colors is liable to make it look unattractively "posterized".

[*] Pay attention to areas of "solid" color.  If an area has grainy color (for example a dark blue sky made up of different shades of dark gray and blue pixels), consider painting over it with a uniform single color to maximize the efficient use of your final palette.  This is especially true of large background areas because of the inset effect.

[*] If you're creating your own art from scratch, you may want to start with a 16-color palette, but there's nothing wrong with taking advantage of a bigger palette and converting it later (for one thing it may be easier to change the design partway through if you're not limited to indexed color with only 16 choices).
[/LIST]

**[SIZE="3"]Editing the image[/SIZE]**

[LIST=1]
[*] First do any "cleanup" tasks like adding or removing elements, or correcting colors.
[*] Next, scale and crop the image to the appropriate resolution (scale first to one dimension, then crop to the other) -- 640 x 400 images for a 640 x 480 VGA boot mode (the default unless you changed it), 640 x 480 images for higher modes.
[*] Last, once the composition and size are right, do the conversion to indexed color with a 16-color palette.
[/LIST]

This sequence preserves color quality and resolution till the very end and makes your final palette easier to work with.

**[SIZE="3"]Editing the palette[/SIZE]**

Almost done!  There are a few considerations when editing the palette.  Your palette entries get used for things besides the image, so you need to be aware of contrast between elements on the screen that you can't see yet!  Here's the list of dual-use palette indexes:

[B]0 -- Background color (text and unpainted screen)
1 -- Progress bar foreground color
2 -- "OK" text foreground color
4 -- Progress bar background color
8 -- Description text foreground color
13 -- "Failed" text foreground color[/B]

That gives you a possible 15 contrast relationships, but not all of them are equally important.

Here are the pairs of elements you want to contrast highly:

[LIST]
[*] 0 <--> 1, 2, 8, 13 (background vs. everything else)
[*] 1 <--> 4 (progress bar foregound to progress bar background)
[*] 2 <--> 13 <--> 8 ("Failed" text to "OK" text and description text, to provide extra visual cue that something failed)
[/LIST]

Here are things you probably want to contrast somewhat:

[LIST]
[*] 0 <--> 4 <--> 8 (an aesthetic choice -- choose color 4 according to how visible you want the progress bar background to be against the image background, and how distinct from the description text)
[*] 4 <--> 13 (progress bar background to "Failed" text)
[*] 2 <--> 8 ("OK" text to description text -- another purely aesthetic choice)
[/LIST]

If this all seems complex and confusing, a simpler way to get the job done is to classify each of the six elements according to whether you want it to be light, medium, or dark, then edit the palette accordingly.  Or, depending on the particular image's colors and your own aesthetic sensibilities, you may want to initially convert the image palette to a 15-, 14- or even as little as 11-color palette and add your own custom palette entries for the various elements.

**[SIZE="3"]How to edit the palette in the GIMP[/SIZE]**

Recent CVS versions of the GIMP have plugin support for directly rearranging the palette without altering the image,  However, since most people have an older version of the GIMP, you can't rearrange palette entries and editing them changes the colors in the image.  Here's how to kludge the rearrangement relatively painlessly.

[LIST=1]
[*] First, convert the image to 16-color indexed mode (**Image -> Mode -> Indexed**).  Specify an **Optimum** palette with a maximum of 16 colors or less, and choose your dithering method ("none" gives a posterized look, either of the Floyd-Steinberg options will give you a more natural appearance -- choose according to your preference), then click **OK**.
[*] Next, go to **Dialogs -> Palettes**.  Right-click in the palette list and choose **Import Palette...**  For the source, select "Image" and the image you just converted.  At the bottom, give it a name if you like, specify 16 colors (or however many you actually chose), then click **Import**.
[*] Now your palette should show up in the list.  Double-click it to edit it, swapping, changing, removing or adding colors in whatever way seems best to you.
[*] Make sure you have between 13 and 16 colors when you're done, then click **Save**.
[*] Go back to the image window.  Go to **Image -> Mode** and choose **RGB**.  This should have no visible effect.
[*] Go back to **Image -> Mode** one last time, choose **Indexed**, and this time specify a **Custom** palette and choose your palette that you just edited.  Uncheck "Remove unused colors from final palette" and click **OK**.
[*] Again, you should see no visible effect, but now the image should be using the custom palette you created (verify with **Dialogs -> Colormap**).
[*] **Save** the image, and now (if you want) you can go back to Palettes and delete the palette you created.
[/LIST]

Once that's done, you can run this PNG through the conversion process to create a new usplash (which is documented [in another forum post]("http://ubuntuforums.org/showthread.php?t=82835")).

---

### Post by orgy on 2006-07-03
thx for the howto, worked for me ;)

---

### Post by Kensey on 2006-07-05
Excellent!  That's always the acid test -- "the directions worked for me, but do they work for anyone else?" :)

---

### Post by blackjack6.21.91 on 2006-07-05
This should be in the howto section..

Not something I'm interested in, but it looks like a well formed howto that works!

---

### Post by Kensey on 2006-07-07
Aw shucks, 't'weren't nothin' :)

But seriously, I was kind of hoping that it would be considered HOWTO-acceptable.  How would I go about trying to get it moved into that section?

---

