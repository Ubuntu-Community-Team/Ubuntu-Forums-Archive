---
title: "What do I install to be able to convert icons to .svg format?"
date: 2007-03-30
forum: General Help
---

### Post by rainwalker on 2007-03-30
Every time I try to convert [filename] to [filename.svg] from the command line, it tells me "convert: no image vector graphics `[filename.svg]'." Is there a way to install the needed 'image vector graphics'?

---

### Post by FakeOutdoorsman on 2007-03-30
Are you trying to convert from a raster image (PNG) to a vector image (SVG)?  You can't easily just convert raster to vector.  You might want to try [Inkscape]("http://www.inkscape.org/").  I believe it has a raster to vector convertor in it.  Inkscape is available for installation in System -> Administration -> Synaptic Package Manager.

---

### Post by dbbolton on 2007-03-30
if you're trying to convert bitmap to vector, that's basically impossible. a bitmap is what its name implies, a map of pixels. a vector graphic file is kind of like a bunch of mathematical equations that draw shapes, gradients, etc. - which is why they are scalable.

---

### Post by rainwalker on 2007-03-30
Yeah, that (was) what I'm trying to do.
Isn't there a way to do it with the Gimp?

---

### Post by FakeOutdoorsman on 2007-03-31
There may already be a SVG version of the icon available.  If it is from [Tango]("http://tango.freedesktop.org/Tango_Desktop_Project") or Oxygen you're probably in luck.

---

### Post by dbbolton on 2007-03-31
> **rainwalker said:**
> Yeah, that (was) what I'm trying to do.
Isn't there a way to do it with the Gimp?

no !

> **dbbolton said:**
> if you're trying to convert bitmap to vector, **that's basically impossible**. a bitmap is what its name implies, a map of pixels. a vector graphic file is kind of like a bunch of mathematical equations that draw shapes, gradients, etc. - which is why they are scalable.

---

### Post by FakeOutdoorsman on 2007-03-31
I believe GIMP can save paths as SVG with the gimp-svg plugin available in Synaptic.

---

### Post by dbbolton on 2007-03-31
> **FakeOutdoorsman said:**
> I believe GIMP can save paths as SVG with the gimp-svg plugin available in Synaptic.
that's because paths are vectors. a png icon is most likely a bitmap, unless it's a fireworks png or something.

some graphics programs can "vectorize" a bitmap, but this is more like a vague, simple imitation and not at all like a conversion. think of trying to convert mp3 files to midi files.

---

### Post by rainwalker on 2007-03-31
Ah...
Oh well

Thanks!

---

### Post by FakeOutdoorsman on 2007-03-31
> **dbbolton said:**
> some graphics programs can "vectorize" a bitmap, but this is more like a vague, simple imitation and not at all like a conversion. think of trying to convert mp3 files to midi files.

The reason I recommended [Inkscape]("http://inkscape.org/") is because it contains Potrace, an open source raster to vector converting tool.  It's included with Inkscape and can convert bitmap images into SVG files.  It's not perfect, but with some tweaking it can do the job.  I've used something similar for a client to convert a raster image to vector that was then applied to the side of a large box truck.

---

