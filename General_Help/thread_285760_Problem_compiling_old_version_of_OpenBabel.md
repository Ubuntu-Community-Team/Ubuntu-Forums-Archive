---
title: "Problem compiling old version of OpenBabel"
date: 2006-10-27
forum: General Help
---

### Post by derbaschti on 2006-10-27
Hi,

I am trying to compile an old version of OpenBabel, which I was given by a colleague. I need this particular version, because he made some hacks that are important.

./configure runs cleanly.

When I do make, it produces totally weird output (see below). I am not very used to compiling programs from source, does anybody have a clue, what might be happening?

```
Making all in src
make[1]: Entering directory `/home/baschti/openbabelmapdip/src'
make  all-recursive
make[2]: Entering directory `/home/baschti/openbabelmapdip/src'
Making all in math
make[3]: Entering directory `/home/baschti/openbabelmapdip/src/math'
if /bin/sh ../../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../../src     -g -O2 -MT matrix3x3.lo -MD -MP -MF ".deps/matrix3x3.Tpo" \
	  -c -o matrix3x3.lo `test -f 'matrix3x3.cpp' || echo './'`matrix3x3.cpp; \
	then mv -f ".deps/matrix3x3.Tpo" ".deps/matrix3x3.Plo"; \
	else rm -f ".deps/matrix3x3.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I../../src -g -O2 -MT matrix3x3.lo -MD -MP -MF .deps/matrix3x3.Tpo -c matrix3x3.cpp -o matrix3x3.o
if /bin/sh ../../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../../src     -g -O2 -MT vector3.lo -MD -MP -MF ".deps/vector3.Tpo" \
	  -c -o vector3.lo `test -f 'vector3.cpp' || echo './'`vector3.cpp; \
	then mv -f ".deps/vector3.Tpo" ".deps/vector3.Plo"; \
	else rm -f ".deps/vector3.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I../../src -g -O2 -MT vector3.lo -MD -MP -MF .deps/vector3.Tpo -c vector3.cpp -o vector3.o
/bin/sh ../../libtool --mode=link g++  -g -O2   -o libmath.la   matrix3x3.lo vector3.lo  -lm 
mkdir .libs
ar cru .libs/libmath.a  matrix3x3.o vector3.o
ranlib .libs/libmath.a
creating libmath.la
(cd .libs && rm -f libmath.la && ln -s ../libmath.la libmath.la)
make[3]: Leaving directory `/home/baschti/openbabelmapdip/src/math'
Making all in windows
make[3]: Entering directory `/home/baschti/openbabelmapdip/src/windows'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/baschti/openbabelmapdip/src/windows'
make[3]: Entering directory `/home/baschti/openbabelmapdip/src'
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT AtomStruct.lo -MD -MP -MF ".deps/AtomStruct.Tpo" \
	  -c -o AtomStruct.lo `test -f 'AtomStruct.cpp' || echo './'`AtomStruct.cpp; \
	then mv -f ".deps/AtomStruct.Tpo" ".deps/AtomStruct.Plo"; \
	else rm -f ".deps/AtomStruct.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT AtomStruct.lo -MD -MP -MF .deps/AtomStruct.Tpo -c AtomStruct.cpp -o AtomStruct.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT CreateSurface.lo -MD -MP -MF ".deps/CreateSurface.Tpo" \
	  -c -o CreateSurface.lo `test -f 'CreateSurface.cpp' || echo './'`CreateSurface.cpp; \
	then mv -f ".deps/CreateSurface.Tpo" ".deps/CreateSurface.Plo"; \
	else rm -f ".deps/CreateSurface.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT CreateSurface.lo -MD -MP -MF .deps/CreateSurface.Tpo -c CreateSurface.cpp -o CreateSurface.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT GridSurface.lo -MD -MP -MF ".deps/GridSurface.Tpo" \
	  -c -o GridSurface.lo `test -f 'GridSurface.cpp' || echo './'`GridSurface.cpp; \
	then mv -f ".deps/GridSurface.Tpo" ".deps/GridSurface.Plo"; \
	else rm -f ".deps/GridSurface.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT GridSurface.lo -MD -MP -MF .deps/GridSurface.Tpo -c GridSurface.cpp -o GridSurface.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT Spheres.lo -MD -MP -MF ".deps/Spheres.Tpo" \
	  -c -o Spheres.lo `test -f 'Spheres.cpp' || echo './'`Spheres.cpp; \
	then mv -f ".deps/Spheres.Tpo" ".deps/Spheres.Plo"; \
	else rm -f ".deps/Spheres.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT Spheres.lo -MD -MP -MF .deps/Spheres.Tpo -c Spheres.cpp -o Spheres.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT alchemy.lo -MD -MP -MF ".deps/alchemy.Tpo" \
	  -c -o alchemy.lo `test -f 'alchemy.cpp' || echo './'`alchemy.cpp; \
	then mv -f ".deps/alchemy.Tpo" ".deps/alchemy.Plo"; \
	else rm -f ".deps/alchemy.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT alchemy.lo -MD -MP -MF .deps/alchemy.Tpo -c alchemy.cpp -o alchemy.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT amber.lo -MD -MP -MF ".deps/amber.Tpo" \
	  -c -o amber.lo `test -f 'amber.cpp' || echo './'`amber.cpp; \
	then mv -f ".deps/amber.Tpo" ".deps/amber.Plo"; \
	else rm -f ".deps/amber.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT amber.lo -MD -MP -MF .deps/amber.Tpo -c amber.cpp -o amber.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT atom.lo -MD -MP -MF ".deps/atom.Tpo" \
	  -c -o atom.lo `test -f 'atom.cpp' || echo './'`atom.cpp; \
	then mv -f ".deps/atom.Tpo" ".deps/atom.Plo"; \
	else rm -f ".deps/atom.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT atom.lo -MD -MP -MF .deps/atom.Tpo -c atom.cpp -o atom.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT balst.lo -MD -MP -MF ".deps/balst.Tpo" \
	  -c -o balst.lo `test -f 'balst.cpp' || echo './'`balst.cpp; \
	then mv -f ".deps/balst.Tpo" ".deps/balst.Plo"; \
	else rm -f ".deps/balst.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT balst.lo -MD -MP -MF .deps/balst.Tpo -c balst.cpp -o balst.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT base.lo -MD -MP -MF ".deps/base.Tpo" \
	  -c -o base.lo `test -f 'base.cpp' || echo './'`base.cpp; \
	then mv -f ".deps/base.Tpo" ".deps/base.Plo"; \
	else rm -f ".deps/base.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT base.lo -MD -MP -MF .deps/base.Tpo -c base.cpp -o base.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT bgf.lo -MD -MP -MF ".deps/bgf.Tpo" \
	  -c -o bgf.lo `test -f 'bgf.cpp' || echo './'`bgf.cpp; \
	then mv -f ".deps/bgf.Tpo" ".deps/bgf.Plo"; \
	else rm -f ".deps/bgf.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT bgf.lo -MD -MP -MF .deps/bgf.Tpo -c bgf.cpp -o bgf.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT binary.lo -MD -MP -MF ".deps/binary.Tpo" \
	  -c -o binary.lo `test -f 'binary.cpp' || echo './'`binary.cpp; \
	then mv -f ".deps/binary.Tpo" ".deps/binary.Plo"; \
	else rm -f ".deps/binary.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT binary.lo -MD -MP -MF .deps/binary.Tpo -c binary.cpp -o binary.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT bitvec.lo -MD -MP -MF ".deps/bitvec.Tpo" \
	  -c -o bitvec.lo `test -f 'bitvec.cpp' || echo './'`bitvec.cpp; \
	then mv -f ".deps/bitvec.Tpo" ".deps/bitvec.Plo"; \
	else rm -f ".deps/bitvec.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT bitvec.lo -MD -MP -MF .deps/bitvec.Tpo -c bitvec.cpp -o bitvec.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT bond.lo -MD -MP -MF ".deps/bond.Tpo" \
	  -c -o bond.lo `test -f 'bond.cpp' || echo './'`bond.cpp; \
	then mv -f ".deps/bond.Tpo" ".deps/bond.Plo"; \
	else rm -f ".deps/bond.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT bond.lo -MD -MP -MF .deps/bond.Tpo -c bond.cpp -o bond.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT box.lo -MD -MP -MF ".deps/box.Tpo" \
	  -c -o box.lo `test -f 'box.cpp' || echo './'`box.cpp; \
	then mv -f ".deps/box.Tpo" ".deps/box.Plo"; \
	else rm -f ".deps/box.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT box.lo -MD -MP -MF .deps/box.Tpo -c box.cpp -o box.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT c3d.lo -MD -MP -MF ".deps/c3d.Tpo" \
	  -c -o c3d.lo `test -f 'c3d.cpp' || echo './'`c3d.cpp; \
	then mv -f ".deps/c3d.Tpo" ".deps/c3d.Plo"; \
	else rm -f ".deps/c3d.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT c3d.lo -MD -MP -MF .deps/c3d.Tpo -c c3d.cpp -o c3d.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT cacao.lo -MD -MP -MF ".deps/cacao.Tpo" \
	  -c -o cacao.lo `test -f 'cacao.cpp' || echo './'`cacao.cpp; \
	then mv -f ".deps/cacao.Tpo" ".deps/cacao.Plo"; \
	else rm -f ".deps/cacao.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT cacao.lo -MD -MP -MF .deps/cacao.Tpo -c cacao.cpp -o cacao.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT cache.lo -MD -MP -MF ".deps/cache.Tpo" \
	  -c -o cache.lo `test -f 'cache.cpp' || echo './'`cache.cpp; \
	then mv -f ".deps/cache.Tpo" ".deps/cache.Plo"; \
	else rm -f ".deps/cache.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT cache.lo -MD -MP -MF .deps/cache.Tpo -c cache.cpp -o cache.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT car.lo -MD -MP -MF ".deps/car.Tpo" \
	  -c -o car.lo `test -f 'car.cpp' || echo './'`car.cpp; \
	then mv -f ".deps/car.Tpo" ".deps/car.Plo"; \
	else rm -f ".deps/car.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT car.lo -MD -MP -MF .deps/car.Tpo -c car.cpp -o car.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ccc.lo -MD -MP -MF ".deps/ccc.Tpo" \
	  -c -o ccc.lo `test -f 'ccc.cpp' || echo './'`ccc.cpp; \
	then mv -f ".deps/ccc.Tpo" ".deps/ccc.Plo"; \
	else rm -f ".deps/ccc.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ccc.lo -MD -MP -MF .deps/ccc.Tpo -c ccc.cpp -o ccc.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT chains.lo -MD -MP -MF ".deps/chains.Tpo" \
	  -c -o chains.lo `test -f 'chains.cpp' || echo './'`chains.cpp; \
	then mv -f ".deps/chains.Tpo" ".deps/chains.Plo"; \
	else rm -f ".deps/chains.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT chains.lo -MD -MP -MF .deps/chains.Tpo -c chains.cpp -o chains.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT chdrw.lo -MD -MP -MF ".deps/chdrw.Tpo" \
	  -c -o chdrw.lo `test -f 'chdrw.cpp' || echo './'`chdrw.cpp; \
	then mv -f ".deps/chdrw.Tpo" ".deps/chdrw.Plo"; \
	else rm -f ".deps/chdrw.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT chdrw.lo -MD -MP -MF .deps/chdrw.Tpo -c chdrw.cpp -o chdrw.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT chiral.lo -MD -MP -MF ".deps/chiral.Tpo" \
	  -c -o chiral.lo `test -f 'chiral.cpp' || echo './'`chiral.cpp; \
	then mv -f ".deps/chiral.Tpo" ".deps/chiral.Plo"; \
	else rm -f ".deps/chiral.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT chiral.lo -MD -MP -MF .deps/chiral.Tpo -c chiral.cpp -o chiral.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT cml.lo -MD -MP -MF ".deps/cml.Tpo" \
	  -c -o cml.lo `test -f 'cml.cpp' || echo './'`cml.cpp; \
	then mv -f ".deps/cml.Tpo" ".deps/cml.Plo"; \
	else rm -f ".deps/cml.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT cml.lo -MD -MP -MF .deps/cml.Tpo -c cml.cpp -o cml.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT csr.lo -MD -MP -MF ".deps/csr.Tpo" \
	  -c -o csr.lo `test -f 'csr.cpp' || echo './'`csr.cpp; \
	then mv -f ".deps/csr.Tpo" ".deps/csr.Plo"; \
	else rm -f ".deps/csr.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT csr.lo -MD -MP -MF .deps/csr.Tpo -c csr.cpp -o csr.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT cssr.lo -MD -MP -MF ".deps/cssr.Tpo" \
	  -c -o cssr.lo `test -f 'cssr.cpp' || echo './'`cssr.cpp; \
	then mv -f ".deps/cssr.Tpo" ".deps/cssr.Plo"; \
	else rm -f ".deps/cssr.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT cssr.lo -MD -MP -MF .deps/cssr.Tpo -c cssr.cpp -o cssr.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT data.lo -MD -MP -MF ".deps/data.Tpo" \
	  -c -o data.lo `test -f 'data.cpp' || echo './'`data.cpp; \
	then mv -f ".deps/data.Tpo" ".deps/data.Plo"; \
	else rm -f ".deps/data.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT data.lo -MD -MP -MF .deps/data.Tpo -c data.cpp -o data.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT dip.lo -MD -MP -MF ".deps/dip.Tpo" \
	  -c -o dip.lo `test -f 'dip.cpp' || echo './'`dip.cpp; \
	then mv -f ".deps/dip.Tpo" ".deps/dip.Plo"; \
	else rm -f ".deps/dip.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT dip.lo -MD -MP -MF .deps/dip.Tpo -c dip.cpp -o dip.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT dmol.lo -MD -MP -MF ".deps/dmol.Tpo" \
	  -c -o dmol.lo `test -f 'dmol.cpp' || echo './'`dmol.cpp; \
	then mv -f ".deps/dmol.Tpo" ".deps/dmol.Plo"; \
	else rm -f ".deps/dmol.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT dmol.lo -MD -MP -MF .deps/dmol.Tpo -c dmol.cpp -o dmol.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT feat.lo -MD -MP -MF ".deps/feat.Tpo" \
	  -c -o feat.lo `test -f 'feat.cpp' || echo './'`feat.cpp; \
	then mv -f ".deps/feat.Tpo" ".deps/feat.Plo"; \
	else rm -f ".deps/feat.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT feat.lo -MD -MP -MF .deps/feat.Tpo -c feat.cpp -o feat.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT fh.lo -MD -MP -MF ".deps/fh.Tpo" \
	  -c -o fh.lo `test -f 'fh.cpp' || echo './'`fh.cpp; \
	then mv -f ".deps/fh.Tpo" ".deps/fh.Plo"; \
	else rm -f ".deps/fh.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT fh.lo -MD -MP -MF .deps/fh.Tpo -c fh.cpp -o fh.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT fileformat.lo -MD -MP -MF ".deps/fileformat.Tpo" \
	  -c -o fileformat.lo `test -f 'fileformat.cpp' || echo './'`fileformat.cpp; \
	then mv -f ".deps/fileformat.Tpo" ".deps/fileformat.Plo"; \
	else rm -f ".deps/fileformat.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT fileformat.lo -MD -MP -MF .deps/fileformat.Tpo -c fileformat.cpp -o fileformat.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT gamess.lo -MD -MP -MF ".deps/gamess.Tpo" \
	  -c -o gamess.lo `test -f 'gamess.cpp' || echo './'`gamess.cpp; \
	then mv -f ".deps/gamess.Tpo" ".deps/gamess.Plo"; \
	else rm -f ".deps/gamess.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT gamess.lo -MD -MP -MF .deps/gamess.Tpo -c gamess.cpp -o gamess.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT gaussian.lo -MD -MP -MF ".deps/gaussian.Tpo" \
	  -c -o gaussian.lo `test -f 'gaussian.cpp' || echo './'`gaussian.cpp; \
	then mv -f ".deps/gaussian.Tpo" ".deps/gaussian.Plo"; \
	else rm -f ".deps/gaussian.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT gaussian.lo -MD -MP -MF .deps/gaussian.Tpo -c gaussian.cpp -o gaussian.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT generic.lo -MD -MP -MF ".deps/generic.Tpo" \
	  -c -o generic.lo `test -f 'generic.cpp' || echo './'`generic.cpp; \
	then mv -f ".deps/generic.Tpo" ".deps/generic.Plo"; \
	else rm -f ".deps/generic.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT generic.lo -MD -MP -MF .deps/generic.Tpo -c generic.cpp -o generic.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ghemical.lo -MD -MP -MF ".deps/ghemical.Tpo" \
	  -c -o ghemical.lo `test -f 'ghemical.cpp' || echo './'`ghemical.cpp; \
	then mv -f ".deps/ghemical.Tpo" ".deps/ghemical.Plo"; \
	else rm -f ".deps/ghemical.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ghemical.lo -MD -MP -MF .deps/ghemical.Tpo -c ghemical.cpp -o ghemical.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT grid.lo -MD -MP -MF ".deps/grid.Tpo" \
	  -c -o grid.lo `test -f 'grid.cpp' || echo './'`grid.cpp; \
	then mv -f ".deps/grid.Tpo" ".deps/grid.Plo"; \
	else rm -f ".deps/grid.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT grid.lo -MD -MP -MF .deps/grid.Tpo -c grid.cpp -o grid.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT gromos96.lo -MD -MP -MF ".deps/gromos96.Tpo" \
	  -c -o gromos96.lo `test -f 'gromos96.cpp' || echo './'`gromos96.cpp; \
	then mv -f ".deps/gromos96.Tpo" ".deps/gromos96.Plo"; \
	else rm -f ".deps/gromos96.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT gromos96.lo -MD -MP -MF .deps/gromos96.Tpo -c gromos96.cpp -o gromos96.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT hin.lo -MD -MP -MF ".deps/hin.Tpo" \
	  -c -o hin.lo `test -f 'hin.cpp' || echo './'`hin.cpp; \
	then mv -f ".deps/hin.Tpo" ".deps/hin.Plo"; \
	else rm -f ".deps/hin.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT hin.lo -MD -MP -MF .deps/hin.Tpo -c hin.cpp -o hin.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT jaguar.lo -MD -MP -MF ".deps/jaguar.Tpo" \
	  -c -o jaguar.lo `test -f 'jaguar.cpp' || echo './'`jaguar.cpp; \
	then mv -f ".deps/jaguar.Tpo" ".deps/jaguar.Plo"; \
	else rm -f ".deps/jaguar.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT jaguar.lo -MD -MP -MF .deps/jaguar.Tpo -c jaguar.cpp -o jaguar.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT map.lo -MD -MP -MF ".deps/map.Tpo" \
	  -c -o map.lo `test -f 'map.cpp' || echo './'`map.cpp; \
	then mv -f ".deps/map.Tpo" ".deps/map.Plo"; \
	else rm -f ".deps/map.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT map.lo -MD -MP -MF .deps/map.Tpo -c map.cpp -o map.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT matrix.lo -MD -MP -MF ".deps/matrix.Tpo" \
	  -c -o matrix.lo `test -f 'matrix.cpp' || echo './'`matrix.cpp; \
	then mv -f ".deps/matrix.Tpo" ".deps/matrix.Plo"; \
	else rm -f ".deps/matrix.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT matrix.lo -MD -MP -MF .deps/matrix.Tpo -c matrix.cpp -o matrix.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT mdl.lo -MD -MP -MF ".deps/mdl.Tpo" \
	  -c -o mdl.lo `test -f 'mdl.cpp' || echo './'`mdl.cpp; \
	then mv -f ".deps/mdl.Tpo" ".deps/mdl.Plo"; \
	else rm -f ".deps/mdl.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT mdl.lo -MD -MP -MF .deps/mdl.Tpo -c mdl.cpp -o mdl.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT mm3.lo -MD -MP -MF ".deps/mm3.Tpo" \
	  -c -o mm3.lo `test -f 'mm3.cpp' || echo './'`mm3.cpp; \
	then mv -f ".deps/mm3.Tpo" ".deps/mm3.Plo"; \
	else rm -f ".deps/mm3.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT mm3.lo -MD -MP -MF .deps/mm3.Tpo -c mm3.cpp -o mm3.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT mmod.lo -MD -MP -MF ".deps/mmod.Tpo" \
	  -c -o mmod.lo `test -f 'mmod.cpp' || echo './'`mmod.cpp; \
	then mv -f ".deps/mmod.Tpo" ".deps/mmod.Plo"; \
	else rm -f ".deps/mmod.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT mmod.lo -MD -MP -MF .deps/mmod.Tpo -c mmod.cpp -o mmod.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT mol.lo -MD -MP -MF ".deps/mol.Tpo" \
	  -c -o mol.lo `test -f 'mol.cpp' || echo './'`mol.cpp; \
	then mv -f ".deps/mol.Tpo" ".deps/mol.Plo"; \
	else rm -f ".deps/mol.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT mol.lo -MD -MP -MF .deps/mol.Tpo -c mol.cpp -o mol.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT mol2.lo -MD -MP -MF ".deps/mol2.Tpo" \
	  -c -o mol2.lo `test -f 'mol2.cpp' || echo './'`mol2.cpp; \
	then mv -f ".deps/mol2.Tpo" ".deps/mol2.Plo"; \
	else rm -f ".deps/mol2.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT mol2.lo -MD -MP -MF .deps/mol2.Tpo -c mol2.cpp -o mol2.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT molchrg.lo -MD -MP -MF ".deps/molchrg.Tpo" \
	  -c -o molchrg.lo `test -f 'molchrg.cpp' || echo './'`molchrg.cpp; \
	then mv -f ".deps/molchrg.Tpo" ".deps/molchrg.Plo"; \
	else rm -f ".deps/molchrg.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT molchrg.lo -MD -MP -MF .deps/molchrg.Tpo -c molchrg.cpp -o molchrg.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT molvector.lo -MD -MP -MF ".deps/molvector.Tpo" \
	  -c -o molvector.lo `test -f 'molvector.cpp' || echo './'`molvector.cpp; \
	then mv -f ".deps/molvector.Tpo" ".deps/molvector.Plo"; \
	else rm -f ".deps/molvector.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT molvector.lo -MD -MP -MF .deps/molvector.Tpo -c molvector.cpp -o molvector.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT mopac.lo -MD -MP -MF ".deps/mopac.Tpo" \
	  -c -o mopac.lo `test -f 'mopac.cpp' || echo './'`mopac.cpp; \
	then mv -f ".deps/mopac.Tpo" ".deps/mopac.Plo"; \
	else rm -f ".deps/mopac.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT mopac.lo -MD -MP -MF .deps/mopac.Tpo -c mopac.cpp -o mopac.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT mpqc.lo -MD -MP -MF ".deps/mpqc.Tpo" \
	  -c -o mpqc.lo `test -f 'mpqc.cpp' || echo './'`mpqc.cpp; \
	then mv -f ".deps/mpqc.Tpo" ".deps/mpqc.Plo"; \
	else rm -f ".deps/mpqc.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT mpqc.lo -MD -MP -MF .deps/mpqc.Tpo -c mpqc.cpp -o mpqc.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT nwchem.lo -MD -MP -MF ".deps/nwchem.Tpo" \
	  -c -o nwchem.lo `test -f 'nwchem.cpp' || echo './'`nwchem.cpp; \
	then mv -f ".deps/nwchem.Tpo" ".deps/nwchem.Plo"; \
	else rm -f ".deps/nwchem.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT nwchem.lo -MD -MP -MF .deps/nwchem.Tpo -c nwchem.cpp -o nwchem.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT oberror.lo -MD -MP -MF ".deps/oberror.Tpo" \
	  -c -o oberror.lo `test -f 'oberror.cpp' || echo './'`oberror.cpp; \
	then mv -f ".deps/oberror.Tpo" ".deps/oberror.Plo"; \
	else rm -f ".deps/oberror.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT oberror.lo -MD -MP -MF .deps/oberror.Tpo -c oberror.cpp -o oberror.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT obutil.lo -MD -MP -MF ".deps/obutil.Tpo" \
	  -c -o obutil.lo `test -f 'obutil.cpp' || echo './'`obutil.cpp; \
	then mv -f ".deps/obutil.Tpo" ".deps/obutil.Plo"; \
	else rm -f ".deps/obutil.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT obutil.lo -MD -MP -MF .deps/obutil.Tpo -c obutil.cpp -o obutil.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT parsmart.lo -MD -MP -MF ".deps/parsmart.Tpo" \
	  -c -o parsmart.lo `test -f 'parsmart.cpp' || echo './'`parsmart.cpp; \
	then mv -f ".deps/parsmart.Tpo" ".deps/parsmart.Plo"; \
	else rm -f ".deps/parsmart.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT parsmart.lo -MD -MP -MF .deps/parsmart.Tpo -c parsmart.cpp -o parsmart.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT parsmi.lo -MD -MP -MF ".deps/parsmi.Tpo" \
	  -c -o parsmi.lo `test -f 'parsmi.cpp' || echo './'`parsmi.cpp; \
	then mv -f ".deps/parsmi.Tpo" ".deps/parsmi.Plo"; \
	else rm -f ".deps/parsmi.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT parsmi.lo -MD -MP -MF .deps/parsmi.Tpo -c parsmi.cpp -o parsmi.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT patty.lo -MD -MP -MF ".deps/patty.Tpo" \
	  -c -o patty.lo `test -f 'patty.cpp' || echo './'`patty.cpp; \
	then mv -f ".deps/patty.Tpo" ".deps/patty.Plo"; \
	else rm -f ".deps/patty.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT patty.lo -MD -MP -MF .deps/patty.Tpo -c patty.cpp -o patty.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT pdb.lo -MD -MP -MF ".deps/pdb.Tpo" \
	  -c -o pdb.lo `test -f 'pdb.cpp' || echo './'`pdb.cpp; \
	then mv -f ".deps/pdb.Tpo" ".deps/pdb.Plo"; \
	else rm -f ".deps/pdb.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT pdb.lo -MD -MP -MF .deps/pdb.Tpo -c pdb.cpp -o pdb.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT phmodel.lo -MD -MP -MF ".deps/phmodel.Tpo" \
	  -c -o phmodel.lo `test -f 'phmodel.cpp' || echo './'`phmodel.cpp; \
	then mv -f ".deps/phmodel.Tpo" ".deps/phmodel.Plo"; \
	else rm -f ".deps/phmodel.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT phmodel.lo -MD -MP -MF .deps/phmodel.Tpo -c phmodel.cpp -o phmodel.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT povray.lo -MD -MP -MF ".deps/povray.Tpo" \
	  -c -o povray.lo `test -f 'povray.cpp' || echo './'`povray.cpp; \
	then mv -f ".deps/povray.Tpo" ".deps/povray.Plo"; \
	else rm -f ".deps/povray.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT povray.lo -MD -MP -MF .deps/povray.Tpo -c povray.cpp -o povray.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT qchem.lo -MD -MP -MF ".deps/qchem.Tpo" \
	  -c -o qchem.lo `test -f 'qchem.cpp' || echo './'`qchem.cpp; \
	then mv -f ".deps/qchem.Tpo" ".deps/qchem.Plo"; \
	else rm -f ".deps/qchem.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT qchem.lo -MD -MP -MF .deps/qchem.Tpo -c qchem.cpp -o qchem.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT rand.lo -MD -MP -MF ".deps/rand.Tpo" \
	  -c -o rand.lo `test -f 'rand.cpp' || echo './'`rand.cpp; \
	then mv -f ".deps/rand.Tpo" ".deps/rand.Plo"; \
	else rm -f ".deps/rand.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT rand.lo -MD -MP -MF .deps/rand.Tpo -c rand.cpp -o rand.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT report.lo -MD -MP -MF ".deps/report.Tpo" \
	  -c -o report.lo `test -f 'report.cpp' || echo './'`report.cpp; \
	then mv -f ".deps/report.Tpo" ".deps/report.Plo"; \
	else rm -f ".deps/report.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT report.lo -MD -MP -MF .deps/report.Tpo -c report.cpp -o report.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT residue.lo -MD -MP -MF ".deps/residue.Tpo" \
	  -c -o residue.lo `test -f 'residue.cpp' || echo './'`residue.cpp; \
	then mv -f ".deps/residue.Tpo" ".deps/residue.Plo"; \
	else rm -f ".deps/residue.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT residue.lo -MD -MP -MF .deps/residue.Tpo -c residue.cpp -o residue.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ring.lo -MD -MP -MF ".deps/ring.Tpo" \
	  -c -o ring.lo `test -f 'ring.cpp' || echo './'`ring.cpp; \
	then mv -f ".deps/ring.Tpo" ".deps/ring.Plo"; \
	else rm -f ".deps/ring.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ring.lo -MD -MP -MF .deps/ring.Tpo -c ring.cpp -o ring.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT rotor.lo -MD -MP -MF ".deps/rotor.Tpo" \
	  -c -o rotor.lo `test -f 'rotor.cpp' || echo './'`rotor.cpp; \
	then mv -f ".deps/rotor.Tpo" ".deps/rotor.Plo"; \
	else rm -f ".deps/rotor.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT rotor.lo -MD -MP -MF .deps/rotor.Tpo -c rotor.cpp -o rotor.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT shelx.lo -MD -MP -MF ".deps/shelx.Tpo" \
	  -c -o shelx.lo `test -f 'shelx.cpp' || echo './'`shelx.cpp; \
	then mv -f ".deps/shelx.Tpo" ".deps/shelx.Plo"; \
	else rm -f ".deps/shelx.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT shelx.lo -MD -MP -MF .deps/shelx.Tpo -c shelx.cpp -o shelx.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT smi.lo -MD -MP -MF ".deps/smi.Tpo" \
	  -c -o smi.lo `test -f 'smi.cpp' || echo './'`smi.cpp; \
	then mv -f ".deps/smi.Tpo" ".deps/smi.Plo"; \
	else rm -f ".deps/smi.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT smi.lo -MD -MP -MF .deps/smi.Tpo -c smi.cpp -o smi.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT tinker.lo -MD -MP -MF ".deps/tinker.Tpo" \
	  -c -o tinker.lo `test -f 'tinker.cpp' || echo './'`tinker.cpp; \
	then mv -f ".deps/tinker.Tpo" ".deps/tinker.Plo"; \
	else rm -f ".deps/tinker.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT tinker.lo -MD -MP -MF .deps/tinker.Tpo -c tinker.cpp -o tinker.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT tokenst.lo -MD -MP -MF ".deps/tokenst.Tpo" \
	  -c -o tokenst.lo `test -f 'tokenst.cpp' || echo './'`tokenst.cpp; \
	then mv -f ".deps/tokenst.Tpo" ".deps/tokenst.Plo"; \
	else rm -f ".deps/tokenst.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT tokenst.lo -MD -MP -MF .deps/tokenst.Tpo -c tokenst.cpp -o tokenst.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT typer.lo -MD -MP -MF ".deps/typer.Tpo" \
	  -c -o typer.lo `test -f 'typer.cpp' || echo './'`typer.cpp; \
	then mv -f ".deps/typer.Tpo" ".deps/typer.Plo"; \
	else rm -f ".deps/typer.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT typer.lo -MD -MP -MF .deps/typer.Tpo -c typer.cpp -o typer.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT unichem.lo -MD -MP -MF ".deps/unichem.Tpo" \
	  -c -o unichem.lo `test -f 'unichem.cpp' || echo './'`unichem.cpp; \
	then mv -f ".deps/unichem.Tpo" ".deps/unichem.Plo"; \
	else rm -f ".deps/unichem.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT unichem.lo -MD -MP -MF .deps/unichem.Tpo -c unichem.cpp -o unichem.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT viewmol.lo -MD -MP -MF ".deps/viewmol.Tpo" \
	  -c -o viewmol.lo `test -f 'viewmol.cpp' || echo './'`viewmol.cpp; \
	then mv -f ".deps/viewmol.Tpo" ".deps/viewmol.Plo"; \
	else rm -f ".deps/viewmol.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT viewmol.lo -MD -MP -MF .deps/viewmol.Tpo -c viewmol.cpp -o viewmol.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT xed.lo -MD -MP -MF ".deps/xed.Tpo" \
	  -c -o xed.lo `test -f 'xed.cpp' || echo './'`xed.cpp; \
	then mv -f ".deps/xed.Tpo" ".deps/xed.Plo"; \
	else rm -f ".deps/xed.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT xed.lo -MD -MP -MF .deps/xed.Tpo -c xed.cpp -o xed.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT xyz.lo -MD -MP -MF ".deps/xyz.Tpo" \
	  -c -o xyz.lo `test -f 'xyz.cpp' || echo './'`xyz.cpp; \
	then mv -f ".deps/xyz.Tpo" ".deps/xyz.Plo"; \
	else rm -f ".deps/xyz.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT xyz.lo -MD -MP -MF .deps/xyz.Tpo -c xyz.cpp -o xyz.o
if /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT zindo.lo -MD -MP -MF ".deps/zindo.Tpo" \
	  -c -o zindo.lo `test -f 'zindo.cpp' || echo './'`zindo.cpp; \
	then mv -f ".deps/zindo.Tpo" ".deps/zindo.Plo"; \
	else rm -f ".deps/zindo.Tpo"; exit 1; \
	fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT zindo.lo -MD -MP -MF .deps/zindo.Tpo -c zindo.cpp -o zindo.o
/bin/sh ../libtool --mode=link g++  -g -O2   -o libopenbabel.la -rpath /usr/local/lib  AtomStruct.lo CreateSurface.lo GridSurface.lo Spheres.lo alchemy.lo amber.lo atom.lo balst.lo base.lo bgf.lo binary.lo bitvec.lo bond.lo box.lo c3d.lo cacao.lo cache.lo car.lo ccc.lo chains.lo chdrw.lo chiral.lo cml.lo csr.lo cssr.lo data.lo dip.lo dmol.lo feat.lo fh.lo fileformat.lo gamess.lo gaussian.lo generic.lo ghemical.lo grid.lo gromos96.lo hin.lo jaguar.lo map.lo matrix.lo mdl.lo mm3.lo mmod.lo mol.lo mol2.lo molchrg.lo molvector.lo mopac.lo mpqc.lo nwchem.lo oberror.lo obutil.lo parsmart.lo parsmi.lo patty.lo pdb.lo phmodel.lo povray.lo qchem.lo rand.lo report.lo residue.lo ring.lo rotor.lo shelx.lo smi.lo tinker.lo tokenst.lo typer.lo unichem.lo viewmol.lo xed.lo xyz.lo zindo.lo math/libmath.la -lm 
mkdir .libs
rm -fr .libs/libopenbabel.lax
mkdir .libs/libopenbabel.lax
rm -fr .libs/libopenbabel.lax/libmath.a
mkdir .libs/libopenbabel.lax/libmath.a
(cd .libs/libopenbabel.lax/libmath.a && ar x /home/baschti/openbabelmapdip/src/math/.libs/libmath.a)
ar cru .libs/libopenbabel.a  AtomStruct.o CreateSurface.o GridSurface.o Spheres.o alchemy.o amber.o atom.o balst.o base.o bgf.o binary.o bitvec.o bond.o box.o c3d.o cacao.o cache.o car.o ccc.o chains.o chdrw.o chiral.o cml.o csr.o cssr.o data.o dip.o dmol.o feat.o fh.o fileformat.o gamess.o gaussian.o generic.o ghemical.o grid.o gromos96.o hin.o jaguar.o map.o matrix.o mdl.o mm3.o mmod.o mol.o mol2.o molchrg.o molvector.o mopac.o mpqc.o nwchem.o oberror.o obutil.o parsmart.o parsmi.o patty.o pdb.o phmodel.o povray.o qchem.o rand.o report.o residue.o ring.o rotor.o shelx.o smi.o tinker.o tokenst.o typer.o unichem.o viewmol.o xed.o xyz.o zindo.o .libs/libopenbabel.lax/libmath.a/matrix3x3.o .libs/libopenbabel.lax/libmath.a/vector3.o 
ranlib .libs/libopenbabel.a
rm -fr .libs/libopenbabel.lax
creating libopenbabel.la
(cd .libs && rm -f libopenbabel.la && ln -s ../libopenbabel.la libopenbabel.la)
if g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT main.o -MD -MP -MF ".deps/main.Tpo" \
	  -c -o main.o `test -f 'main.cpp' || echo './'`main.cpp; \
	then mv -f ".deps/main.Tpo" ".deps/main.Po"; \
	else rm -f ".deps/main.Tpo"; exit 1; \
	fi
/bin/sh ../libtool --mode=link g++  -g -O2   -o babel  main.o libopenbabel.la -lm 
g++ -g -O2 -o babel main.o  ./.libs/libopenbabel.a -lm
make[3]: Leaving directory `/home/baschti/openbabelmapdip/src'
make[2]: Leaving directory `/home/baschti/openbabelmapdip/src'
make[1]: Leaving directory `/home/baschti/openbabelmapdip/src'
Making all in test
make[1]: Entering directory `/home/baschti/openbabelmapdip/test'
if g++ -DHAVE_CONFIG_H -I. -I. -I../src     -g -O2 -MT matrixtest.o -MD -MP -MF ".deps/matrixtest.Tpo" \
	  -c -o matrixtest.o `test -f 'matrixtest.cpp' || echo './'`matrixtest.cpp; \
	then mv -f ".deps/matrixtest.Tpo" ".deps/matrixtest.Po"; \
	else rm -f ".deps/matrixtest.Tpo"; exit 1; \
	fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../src     -g -O2 -MT ringtest.o -MD -MP -MF ".deps/ringtest.Tpo" \
	  -c -o ringtest.o `test -f 'ringtest.cpp' || echo './'`ringtest.cpp; \
	then mv -f ".deps/ringtest.Tpo" ".deps/ringtest.Po"; \
	else rm -f ".deps/ringtest.Tpo"; exit 1; \
	fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../src     -g -O2 -MT main.o -MD -MP -MF ".deps/main.Tpo" \
	  -c -o main.o `test -f 'main.cpp' || echo './'`main.cpp; \
	then mv -f ".deps/main.Tpo" ".deps/main.Po"; \
	else rm -f ".deps/main.Tpo"; exit 1; \
	fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../src     -g -O2 -MT smartstest.o -MD -MP -MF ".deps/smartstest.Tpo" \
	  -c -o smartstest.o `test -f 'smartstest.cpp' || echo './'`smartstest.cpp; \
	then mv -f ".deps/smartstest.Tpo" ".deps/smartstest.Po"; \
	else rm -f ".deps/smartstest.Tpo"; exit 1; \
	fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../src     -g -O2 -MT unitcell.o -MD -MP -MF ".deps/unitcell.Tpo" \
	  -c -o unitcell.o `test -f 'unitcell.cpp' || echo './'`unitcell.cpp; \
	then mv -f ".deps/unitcell.Tpo" ".deps/unitcell.Po"; \
	else rm -f ".deps/unitcell.Tpo"; exit 1; \
	fi
/bin/sh ../libtool --mode=link g++  -g -O2   -o obtest  matrixtest.o ringtest.o main.o smartstest.o unitcell.o ../src/libopenbabel.la -lm 
mkdir .libs
g++ -g -O2 -o obtest matrixtest.o ringtest.o main.o smartstest.o unitcell.o  ../src/.libs/libopenbabel.a -lm
if g++ -DHAVE_CONFIG_H -I. -I. -I../src     -g -O2 -MT roundtrip.o -MD -MP -MF ".deps/roundtrip.Tpo" \
	  -c -o roundtrip.o `test -f 'roundtrip.cpp' || echo './'`roundtrip.cpp; \
	then mv -f ".deps/roundtrip.Tpo" ".deps/roundtrip.Po"; \
	else rm -f ".deps/roundtrip.Tpo"; exit 1; \
	fi
/bin/sh ../libtool --mode=link g++  -g -O2   -o roundtrip  roundtrip.o ../src/libopenbabel.la -lm 
g++ -g -O2 -o roundtrip roundtrip.o  ../src/.libs/libopenbabel.a -lm
make[1]: Leaving directory `/home/baschti/openbabelmapdip/test'
Making all in doc
make[1]: Entering directory `/home/baschti/openbabelmapdip/doc'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/baschti/openbabelmapdip/doc'
make[1]: Entering directory `/home/baschti/openbabelmapdip'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/baschti/openbabelmapdip'

```

---

