cmake_minimum_required(VERSION 2.8)

project(vhsm)

add_subdirectory(vhsm_api_prototype_impl)
add_subdirectory(vhsm_admin)

install(FILES vhsm_api_prototype/common.h
	vhsm_api_prototype/digest.h
	vhsm_api_prototype/key_mgmt.h
	vhsm_api_prototype/mac.h
	DESTINATION include/vhsm_api)

if(BUILD_tests)
	add_subdirectory(test_app)
	add_dependencies(test_app vhsmapi)
endif(BUILD_tests)

if(BUILD_pam)
	add_subdirectory(pam)
	add_dependencies(pam-vhsm vhsmapi)
endif(BUILD_pam)

