TEXFILE  = main
FILES    = $(TEXFILE).tex intro.tex rw.tex design.tex eval.tex concl.tex appA.tex 
BIBFILE  = all.bib

# If you instead of writing an own all.bib would like to include 
# old .bib files and you have access to SVN at Simula you could use:

#BIBHOME ?= /hom/paalh/SYNC/papers/MiSMoSS/bibfile
#vpath %.bib ${BIBHOME}

# Must start with macros.bib
#BIBFILES = macros.bib graph-algorithms.bib games.bib thin-stream-applications.bib ......

# This migth have to be moved down....
#${BIBFILE}: ${BIBFILES}
#	cat $^ > $@


all:    $(TEXFILE).dvi

ps:     $(TEXFILE).ps

pdf:    $(TEXFILE).pdf

$(TEXFILE).aux: $(FILES)
	latex $(FILES)
	latex $(FILES)

$(TEXFILE).bbl: $(TEXFILE).aux $(BIBFILE)
	bibtex $(TEXFILE)

%.dvi: %.bbl
	latex $*
	latex $*

# To be able to make PDFs with embedded fonts etc.
%.ps: %.dvi
	dvips -t letter -Ppdf -j0 -G0 $<

%.pdf: %.ps
	ps2pdf14 -dPDFSETTINGS=/prepress -dEmbedAllFonts=true $<

clean:
	rm -f *.log *.aux *.bbl *.blg *.dvi *.bak *.toc
	rm -f *.ps *.pdf
	rm -f *~

