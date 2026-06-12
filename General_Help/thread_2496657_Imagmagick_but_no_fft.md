---
title: "Imagmagick but no fft"
date: 2024-04-07
forum: General Help
---

### Post by hakelm on 2024-04-07
I am trying to do some fft processing with imagemagick but it doesn't work.
When trying I get:
 magick: delegate library support not built-in `kors.png' (FFTW) @ warning/fourier.c/ForwardFourierTransformImage/922.
I have fftw installed, see below.
I uninstalled Imagemagick.
Ran root@x22:/home/he/ImageMagick# ./configure --with-modules 
Output shows   FFTW              --with-fftw=no			noWhat can I do?
Thanks in advance for any tip.
H

root@x22:/home/he# dpkg-query --list|grep fftw3
ii  libfftw3-3:amd64                                            3.3.8-2ubuntu8                                                 amd64        Library for computing Fast Fourier Transforms
ii  libfftw3-bin                                                3.3.8-2ubuntu8                                                 amd64        Library for computing Fast Fourier Transforms - Tools
ii  libfftw3-dev:amd64                                          3.3.8-2ubuntu8                                                 amd64        Library for computing Fast Fourier Transforms - development
ii  libfftw3-double3:amd64                                      3.3.8-2ubuntu8                                                 amd64        Library for computing Fast Fourier Transforms - Double precision
ii  libfftw3-long3:amd64                                        3.3.8-2ubuntu8                                                 amd64        Library for computing Fast Fourier Transforms - Long precision
ii  libfftw3-mpi3:amd64                                         3.3.8-2ubuntu8                                                 amd64        MPI Library for computing Fast Fourier Transforms
ii  libfftw3-quad3:amd64                                        3.3.8-2ubuntu8                                                 amd64        Library for computing Fast Fourier Transforms - Quad precision
ii  libfftw3-single3:amd64

---

### Post by hakelm on 2024-04-08
as diemstra told me Imagmagick must be configured with 
./configure --with-modules --with-fftw=yes

---

