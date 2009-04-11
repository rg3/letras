PROJECT(letras)
SET(PROJECT_BIN_DIR bin)
SET(PROJECT_DATA_DIR share/letras)

INCLUDE(FindPythonInterp)
IF (NOT PYTHONINTERP_FOUND)
	MESSAGE(FATA_ERROR "Python interpreter not found")
ENDIF(NOT PYTHONINTERP_FOUND)

CONFIGURE_FILE(build-letras-db.py.in build-letras-db.py)
CONFIGURE_FILE(letras-gui.in letras-gui)
CONFIGURE_FILE(letras.kmdr.in letras.kmdr)
CONFIGURE_FILE(letras.py.in letras.py)
CONFIGURE_FILE(palabras.db palabras.db COPYONLY)
CONFIGURE_FILE(palabras-utf8.txt palabras-utf8.txt COPYONLY)
CONFIGURE_FILE(palabras-utf8-final.txt palabras-utf8-final.txt COPYONLY)

INSTALL(PROGRAMS ${letras_BINARY_DIR}/build-letras-db.py ${letras_BINARY_DIR}/letras-gui ${letras_BINARY_DIR}/letras.py DESTINATION ${PROJECT_BIN_DIR})
INSTALL(FILES ${letras_BINARY_DIR}/letras.kmdr ${letras_BINARY_DIR}/palabras.db ${letras_BINARY_DIR}/palabras-utf8.txt ${letras_BINARY_DIR}/palabras-utf8-final.txt DESTINATION ${PROJECT_DATA_DIR})
