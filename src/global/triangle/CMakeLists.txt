SET(SOURCES
  triangle.c
  DICe_TriangleUtils.cpp
  )

SET(HEADERS
  triangle.h
  DICe_TriangleUtils.h
  )

include_directories (
    .
    ${DICE_HEADER_DIRS}
    ${DICE_TRILINOS_HEADERS}
)

#add_definitions(-DTRILIBRARY -DANSI_DECLARATORS)

add_library(triangle ${SOURCES} ${HEADERS})
target_compile_definitions(triangle PRIVATE -D DICE_LIB_EXPORTS_MODE)
target_link_libraries(triangle dicebase dicemesh diceparser)

install(FILES ${HEADERS}
  DESTINATION ${CMAKE_INSTALL_PREFIX}/include
)
install(TARGETS triangle
  DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
)
set_target_properties(triangle PROPERTIES
  RUNTIME_OUTPUT_DIRECTORY "${DICE_OUTPUT_PREFIX}/bin"
  LIBRARY_OUTPUT_DIRECTORY "${DICE_OUTPUT_PREFIX}/lib"
  ARCHIVE_OUTPUT_DIRECTORY "${DICE_OUTPUT_PREFIX}/lib"
)