# Makefile for tools

include ../../make.inc

# location of needed modules
MODFLAGS= $(BASEMOD_FLAGS) \
          $(MOD_FLAG)../src
QEMODS = ../../Modules/libqemod.a ../../FFTXlib/libqefft.a \
         ../../KS_Solvers/libks_solvers.a \
         ../../LAXlib/libqela.a ../../UtilXlib/libutil.a
PWOBJS = ../src/libpw.a

TLDEPS= pwlibs

all : tldeps ev.x kpoints.x pwi2xsf.x ibrav2cell.x

ibrav2cell.x : ibrav2cell.o $(PWOBJS) $(QEMODS) $(LIBOBJS)
	$(LD) $(LDFLAGS) -o $@ \
		ibrav2cell.o $(PWOBJS) $(QEMODS) $(LIBOBJS) $(QELIBS)
	- ( cd ../../bin ; ln -fs ../PW/tools/$@ . )
	- ( cd ../../bin ; ln -fs ../PW/tools/cell2ibrav.py cell2ibrav.x )

ev.x : ev.o $(PWOBJS) $(QEMODS) $(LIBOBJS)
	$(LD) $(LDFLAGS) -o $@ \
		ev.o $(PWOBJS) $(QEMODS) $(LIBOBJS) $(QELIBS)
	- ( cd ../../bin ; ln -fs ../PW/tools/$@ . )

kpoints.x : kpoints.o $(PWOBJS) $(QEMODS) $(LIBOBJS)
	$(LD) $(LDFLAGS) -o $@ \
		kpoints.o $(PWOBJS) $(QEMODS) $(LIBOBJS) $(QELIBS)
	- ( cd ../../bin ; ln -fs ../PW/tools/$@ . )

pwi2xsf.x : pwi2xsf.o $(PWOBJS) $(QEMODS) $(LIBOBJS)
	$(LD) $(LDFLAGS) -o $@ \
		pwi2xsf.o $(PWOBJS) $(QEMODS) $(LIBOBJS) $(QELIBS)
	- ( cd ../../bin ; ln -fs ../PW/tools/$@ . )

tldeps:
	if test -n "$(TLDEPS)" ; then \
	( cd ../.. ; $(MAKE) $(TLDEPS) || exit 1 ) ; fi

clean :
	- /bin/rm -f pwi2xsf pwi2xsf_old *.x *.o *~ *_tmp.f90 *.mod *.d *.i *.L

include make.depend
