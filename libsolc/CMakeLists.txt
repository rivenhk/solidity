set(
	sources
)

if (EMSCRIPTEN)
	set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -s EXPORTED_FUNCTIONS='[\"_compileJSON\",\"_license\",\"_version\",\"_compileJSONMulti\",\"_compileJSONCallback\",\"_compileStandard\"]' -s RESERVED_FUNCTION_POINTERS=20")
	add_executable(soljson libsolc.cpp)
else()
	add_library(soljson libsolc.cpp)
endif()
target_link_libraries(soljson PRIVATE solidity)
