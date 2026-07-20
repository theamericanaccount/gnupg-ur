# SPDX-License-Identifier: AGPL-3.0

#    -----------------------------------------------------
#    Copyright © 2024, 2025, 2026  Pellegrino Prevete
#
#    All rights reserved
#    -----------------------------------------------------
#
#    This program is free software: you can redistribute
#    it and/or modify it under the terms of the
#    GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of
#    the License, or (at your option) any later version.
#
#    This program is distributed in the hope that it
#    will be useful, but WITHOUT ANY WARRANTY;
#    without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
#    See the GNU Affero General Public License for
#    more details.
#
#    You should have received a copy of the
#    GNU Affero General Public License
#    along with this program.
#    If not, see <https://www.gnu.org/licenses/>.

# Maintainers:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
#   Pellegrino Prevete (dvorak)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
#   David Runge
#     <dvzrv@archlinux.org>
#   Levente Polyak
#     <anthraxx[at]archlinux[dot]org>
#   Lukas Fleischer
#     <lfleischer@archlinux.org>

# Contributors:
#   Gaetan Bisson
#     <bisson@archlinux.org>
#   Tobias Powalowski
#     <tpowa@archlinux.org>
#   Andreas Radke
#     <andyrtr@archlinux.org>
#   Judd Vinet
#     <jvinet@zeroflux.org>

_os="$(
  uname \
    -o)"
if [[ "${_os}" == "Android" ]]; then
  _libc="ndk-sysroot"
  _compiler="clang"
  _libcompiler="llvm-libs"
  _npth="libnpth"
  _pcsclite="libpcsclite"
elif [[ "${_os}" == "GNU/Linux" ]]; then
  _libc="glibc"
  _compiler="gcc"
  _libcompiler="libgcc"
  _npth="npth"
  _pcsclite="pcsclite"
elif [[ "${_os}" == "Msys" ]]; then
  _libc="msys2-w32api-runtime"
  _libc_headers="msys2-w32api-headers"
  _compiler="gcc"
  _libcompiler="gcc-libs"
  _npth="npth"
  _pcsclite="pcsclite"
  _sh="sh"
else
  _msg=(
    "Unknown os '${_os}'."
  )
  msg \
    "${_msg[*]}"
  _libc="msys2-w32api-runtime"
  _libc_headers="msys2-w32api-headers"
  _compiler="gcc"
  _libcompiler="gcc-libs"
  _npth="npth"
  _pcsclite="pcsclite"
  _pcsclite="pcsclite"
  _sh="sh"
fi
_evmfs_available="$(
  command \
    -v \
    "evmfs" || \
    true)"
if [[ ! -v "_evmfs" ]]; then
  if [[ "${_evmfs_available}" != "" ]]; then
    _evmfs="true"
  elif [[ "${_evmfs_available}" == "" ]]; then
    _evmfs="false"
  fi
fi
if [[ ! -v "_git_service" ]]; then
  _git_service="github"
fi
if [[ ! -v "_docs" ]]; then
  if [[ "${_os}" == "GNU/Linux" ]]; then
    _docs="true"
  else
    _docs="false"
  fi
fi
_pkg=gnupg
if [[ ! -v "_git_http" ]]; then
  if [[ "${_git_service}" == "github" ]]; then
    _git_http="github.com"
  elif [[ "${_git_service}" == "gitlab" ]]; then
    _git_http="gitlab.com"
  elif [[ "${_git_service}" == "gnupg" ]]; then
    _git_http="dev.${_pkg}.org"
  fi
fi
if [[ ! -v "_ns" ]]; then
  if [[ "${_git_service}" == "github" ]]; then
    _ns="themartiancompany"
  elif [[ "${_git_service}" == "gitlab" ]]; then
    _ns="freepg"
  elif [[ "${_git_service}" == "gnupg" ]]; then
    _ns="source"
  fi
fi
if [[ ! -v "_git" ]]; then
  if [[ "${_git_service}" == "gnupg" ]]; then
    _git="true"
  else
    _git="false"
  fi
fi
if [[ ! -v "_archive_format" ]]; then
  if [[ "${_git}" == "true" ]]; then
    if [[ "${_evmfs}" == "true" ]]; then
      _archive_format="bundle"
    elif [[ "${_evmfs}" == "false" ]]; then
      _archive_format="git"
    fi
  elif [[ "${_git}" == "false" ]]; then
    if [[ "${_git_service}" == "github" ]]; then
      _archive_format="zip"
    elif [[ "${_git_service}" == "gitlab" ]]; then
      _archive_format="tar.gz"
    fi
  fi
fi
if [[ "${_os}" == "Android" ]]; then
  _locale="C.UTF-8"
else
  _locale="$(
    locale |
      grep \
        "LANG=" |
        awk \
          -F \
            "=" \
          '{print $1}')"
fi
if [[ ! -v "_en" ]]; then
  _en="true"
  if [[ "${_locale}" == "C.UTF-8" ]]; then
    _en="true"
  fi
fi
if [[ ! -v "_it" ]]; then
  _it="true"
  if [[ "${_locale}" == "it_IT.UTF-8" ]]; then
    _it="true"
  fi
fi
if [[ ! -v "_like" ]]; then
  if [[ "${_it}" == "true" ]]; then
    _like="mo-me-lo-segno"
  fi
  if [[ "${_en}" == "true" ]]; then
    _like="never-gonna-give-you-up"
  fi
fi
pkgbase="${_pkg}"
pkgname=(
  "${_pkg}"
)
pkgver=2.5.18
_2_5_18_commit="1b8362889a522bbcfeb80ef3af61218db216f62b"
_2_5_18_freepg_commit="756502e158cc2742a956333997037f72ee5ff40f"
_commit="${_2_5_18_freepg_commit}"
_libassuan_pkgver="3.0.2"
pkgrel=92
_pkgdesc=(
  'Complete and free implementation'
  'of the OpenPGP standard.'
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  "aarch64"
  "arm"
  "armv8l"
  "armv7l"
  "i686"
  "mips"
  "pentium4"
  "powerpc"
  "x86_64"
)
url="https://www.${_pkg}.org"
license=(
  "BSD-2-Clause"
  "BSD-3-Clause"
  "BSD-4-Clause"
  "CC0-1.0"
  "GPL-2.0-or-later"
  "GPL-3.0-or-later"
  "LGPL-2.1-or-later"
  'LGPL-3.0-or-later OR GPL-2.0-or-later'
  "MIT"
  "Unicode-TOU"
)
depends=(
  "${_libc}"
  "gnutls"
  "libgcrypt"
  "libgpg-error"
  "${_libcompiler}"
  "libksba"
  "libldap"
  "libusb"
  "pinentry"
  "sh"
  "sqlite"
  "tpm2-tss"
  "zlib"
)
makedepends=(
  "autoconf"
  "automake"
  "bzip2"
  "libassuan>=${_libassuan_pkgver}"
  "librsvg"
  "${_npth}"
  "${_pcsclite}"
  "readline"
  # part of base-devel
  "gettext"
  "${_compiler}"
  "${_libcompiler}"
)
if [[ "${_docs}" == "true" ]]; then
  makedepends+=(
    "fig2dev"
    "ghostscript"
    "imagemagick"
  )
fi
if [[ "${_os}" == "Msys" ]]; then
  makedepends+=(
    "${_libc_headers}"
    "windows-default-manifest"
  )
fi
if [[ "${_git}" == "true" ]]; then
  makedepends+=(
    "git" 
  )
fi
if [[ "${_evmfs}" == "true" ]]; then
  makedepends+=(
    "evmfs" 
  )
fi
checkdepends=(
  "openssh"
)
_pcslite_optdepends=(
  "pcsclite:"
    "for using scdaemon not with the"
    "gnupg internal card driver."
)
optdepends=(
  "${_pcslite_optdepends[*]}"
)
install="${_pkg}.install"
_http="https://${_git_http}"
_url="${_http}/${_ns}/${_pkg}"
_tag_name="commit"
if [[ "${_tag_name}" == "commit" ]]; then
  _tag="${_commit}"
elif [[ "${_tag_name}" == "tag" ]]; then
  if [[ "${_git_service}" == "gnupg" ]]; then
    _tag="${_pkg}-${pkgver}"
  else
    _tag="${_pkg}-${pkgver}-freepg"
  fi
fi
_tarname="${_pkg}-${_tag}"
_tarfile="${_pkg}-${_tag}.${_archive_format}"
_gitlab_sum="SKIP"
_gitlab_sig_sum="SKIP"
_github_sum="c39042db96a85b64834c479e69a6f3481e92a44b0dde756634a231fbbb4a99e6"
_github_sig_sum="0f2a92ea1f158233a6b1562e9caec66ad91eaa446b03ecaa235d911c4c8774ef"
_bundle_sum="712afbfbcca4c9ee8592eba482fe4fc40ff62557e80080bc53b3377cfee8e9fd"
_bundle_sig_sum="7e42d6954ebdd6e106e3cc1bb32902ca42a8a9de5ea089fca849426832577da1"
# that crazy kid address
_kid_ns="0x926acb6aA4790ff678848A9F1C59E578B148C786"
# Dvorak
_dvorak_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
if [[ "${_evmfs}" == "true" ]]; then
  if [[ "${_git}" == "true" ]]; then
    _sum="${_bundle_sum}"
    _sig_sum="${_bundle_sig_sum}"
    # Tallero
    # _evmfs_ns="0x6ec7cC56dCeC0a00CB15E97C64B1a5Ec7A31403c"
  elif [[ "${_git}" == "false" ]]; then
    if [[ "${_git_service}" == "github" ]]; then
      _sum="${_github_sum}"
      _sig_sum="${_github_sig_sum}"
      # Dvorak
      # _evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
      # Truocolo
      # _evmfs_ns="0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b"
    elif [[ "${_git_service}" == "gitlab" ]]; then
      _sum="${_gitlab_sum}"
      _sig_sum="${_gitlab_sig_sum}"
      # Tallero
      # _evmfs_ns="0x6ec7cC56dCeC0a00CB15E97C64B1a5Ec7A31403c"
    fi
  fi
elif [[ "${_evmfs}" == "false" ]]; then
  if [[ "${_git}" == "true" ]]; then
    if [[ "${_tag_name}" == "tag" ]]; then
      _sum='383fd9720a966825b9d5e45a2b49b3b340ebed356252c73cca242b26dffec0ba'
      _b2_sum='c6b16d797b13e91c4f3eb41d28a69a5854e1744eaac662058cc5332b69b90349a79b891895b7460027bd6234394a4caf36f800d20a74c696a049764112f00658'
    elif [[ "${_tag_name}" == "commit" ]]; then
      _sum="SKIP"
      _b2_sum="SKIP"
    fi
  elif [[ "${_git}" == "false" ]]; then
    if [[ "${_git_service}" == "github" ]]; then
      _sum="${_github_sum}"
      _sig_sum="${_github_sig_sum}"
      # Truocolo
      _evmfs_ns="0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b"
    elif [[ "${_git_service}" == "gitlab" ]]; then
      _sum="${_gitlab_sum}"
      _sig_sum="${_gitlab_sig_sum}"
      # Dvorak
      _evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
      # Tallero
      _evmfs_ns="0x6ec7cC56dCeC0a00CB15E97C64B1a5Ec7A31403c"
    fi
  fi
fi
_evmfs_ns="${_kid_ns}"
_evmfs_sig_ns="${_dvorak_ns}"
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_evmfs_dir="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}"
_evmfs_uri="${_evmfs_dir}/${_sum}"
_evmfs_src="${_tarfile}::${_evmfs_uri}"
_sig_uri="${_evmfs_dir}/${_sig_sum}"
_sig_src="${_tarfile}.sig::${_sig_uri}"
if [[ "${_evmfs}" == "true" ]]; then
  _src="${_evmfs_src}"
  source+=(
    "${_sig_src}"
  )
  sha256sums+=(
    "${_sig_sum}"
  )
elif [[ "${_evmfs}" == "false" ]]; then
  if [[ "${_git}" == true ]]; then
    _src="${_tarname}::git+${_url}#${_tag_name}=${_tag}"
    _sum="SKIP"
  elif [[ "${_git}" == false ]]; then
    _uri=""
    if [[ "${_git_service}" == "github" ]]; then
      if [[ "${_tag_name}" == "commit" ]]; then
        _uri="${_url}/archive/${_commit}.${_archive_format}"
        _sum="${_github_sum}"
      fi
    elif [[ "${_git_service}" == "gitlab" ]]; then
      if [[ "${_tag_name}" == "commit" ]]; then
        _uri="${_url}/-/archive/${_tag}/${_tag}.${_archive_format}"
      fi
    fi
    _src="${_tarfile}::${_uri}"
  fi
fi
source+=(
  "${_src}"
  "dirmngr"{"","@"}"."{"service","socket"}
  "gpg-agent"{"","@"}.{"service","socket"}
  "gpg-agent-"{"browser","extra","ssh"}{"","@"}".socket"
  "keyboxd"{"","@"}.{"service","socket"}
  "keyboxd.8"
  # do not emit beta warnings
  # (due to misbehaving build system)
  # "${_pkg}-2.4-avoid_beta_warning.patch"
  # from 2.5 onwards the freepg repo is target
  # directly so one doesnt have to create patches
  # for every release
  # still im keeping this here for debug purposes for now
  # https://gitlab.com/freepg/gnupg/-/commits/gnupg-2.5.18-freepg
  # "0001-gpg-accept-subkeys-with-a-good-revocation-but-no-sel.patch"
  # "0002-gpg-allow-import-of-previously-known-keys-even-witho.patch"
  # "0003-tests-add-test-cases-for-import-without-uid.patch"
  # "0004-gpg-drop-import-clean-from-default-keyserver-import-.patch"
  # "0005-avoid-systemd-deprecation-warning.patch"
  # "0006-Add-systemd-support-for-keyboxd.patch"
  # "0007-Ship-sample-systemd-unit-files.patch"
  # "0008-gpg-default-El-Gamal-to-3072-bit-keys.patch"
  # "0009-gpg-Always-support-and-default-to-using-SHA-512.patch"
  # "0010-gpg-Prefer-SHA-512-and-SHA-384-in-personal-digest-pr.patch"
  # "0012-Disallow-compressed-signatures-and-certificates.patch"
  # "0011-Avoid-simple-memory-dumps-via-ptrace.patch"
  # "0013-ssh-agent-emulation-under-systemd-inject-SSH_AUTH_SO.patch"
  # "0014-gpg-Sync-compliance-mode-cleanup-with-master.patch"
  # "0015-gpg-emit-RSA-pubkey-algorithm-when-in-compatibility-.patch"
  # "0016-gpg-Reintroduce-openpgp-as-distinct-from-rfc4880.patch"
  # "0017-gpg-Emit-LibrePGP-material-only-in-compliance-gnupg.patch"
  # "0018-gpg-gpgconf-list-report-actual-compliance-mode.patch"
  # "0019-gpg-Default-to-compliance-openpgp.patch"
  # "0020-gpg-Fix-newlines-in-Cleartext-Signature-Framework-CS.patch"
  # "0021-Add-keyboxd-systemd-support.patch"
  # "0022-Support-large-RSA-keygen-in-non-batch-mode.patch"
  # "0023-gpg-Verify-Text-mode-Signatures-over-binary-Literal-.patch"
  # "0024-gpg-Do-not-use-a-default-when-asking-for-another-out.patch"
)
sha256sums+=(
  "${_sum}"
  '80a3a80f9f1f337da555a6838483e1baca44cde8a8a3d8c4ba7743626304b981'
  '8374255ce93a3c343019ab425963bcbc41982ea89e669d1ad1df0aa7be810de1'
  'ca55048f992824a24ab7f61cbc44a713a153f70a1a60d1cbba7ab4440302a204'
  'd0d79d76bbf6c0d744ee262882fcdfbe52601c6d74cdc5dd99a15da1cdbb6ae1'
  '8ea489a57edb0db9394bf2d6c0ec62205f881bb54efb919e4870209c7db01aa7'
  '81e9dd05cbf3b8406367258eae6ef67ff97f270301bf50b52742647c515c8304'
  'f735119afa3c452728e899809aa1d87b6091a327934befde3aef70ea9259197f'
  '2af0824fdbb95c1c6b54a9ab0a22aeb92ac997e44112f93919d263efa81909ae'
  '1cf9821b3bf4efaf4da2fd52ceb70d254dc4f6c545603f9045de716ef6aabf2d'
  '402eb8f875daaa419f9fdef59ffa84a1e063cc79e04d885ab0768788a4620ac0'
  'f0094f67586cbcda17fd0d780e3e73d6dbaa479ac84715ba941531f83f6ecfe9'
  '6644d769f7919ad58d3caf955195047c521328d180ee2077b78b7f1459f3184b'
  'ffa0191fad52712732f8b24d7d570c1d19a7803e59d30088797b76e252f65858'
  'ddfeafd4b86ef4dd7bcc841115483bcda58c660547ebaeae47ee343741e571eb'
  'cba1aa10c072d982135d2367a7e957d6787037ab232fd148144eca39a92ec2e6'
  '2e3e6ce050737c3bc0e608f283bdfef5471def2ff12dee7ef007854033178694'
  '34144a8e43fbeac88f1ddaf1621e6a3b192efba4580d18a42254ad386819afea'
  '50a00213e44ff07b385e12bca455cd5eec35b271ca2fe500bfe7704ebd8ec73d'
  '38c66efbd3bffdfa9cb0f226a6db03ae4b226f705dc2d0266a555d8ace823b79'
)
# b2sums=(
#   "${_b2_sum}"
#   '7a3af856305eb4b00929aaf029dd4e5c84376df4f30add76976b9b058addf6fc4d8c39335fc83d11493ea9d8a40f0510dbac8572b99a8c8b9b3a4eca8e585774'
#   'ee51a4702715f5ec2629ff42eeba8630010da8a67545d1e53961e710de5faf197708e55d2d55796917a134ca2a76b1d6c88a8f7756d0706e0cbc33b605f52d86'
#   '3f40de2bf73e84f099b542349257ef6c098b4e347fb218d21a2a785830aa335832229b24c74aadae73deff5460f8645e2d7e7c3c2faaeb91cc812eeb06ddca84'
#   '10c6074d67addd5c244a2e83485ed0fd34847e16619e2ff4a5ab09011ed9daf199b7d7b5f109a1ea88a6ba3218e442c6c28575879b305686a13c8a93612937a3'
#   'ad71d7fab2a92a8da454c34884b5724e94adc0925a7f97f062fb7b78ed3ec87e5babb6383e755c943afd16bf61789ba83455dc2baf82ce248c1c4622ff87e364'
#   '129ecd9df3f00ed28f494f914483645e9aeaa1d6812c762ded60582c0a3f66b215731d4415ea5c017aa5ce97448faa5b93dbcb3793a82643d6ed160cc62f4ea4'
#   '36f8709733fbd509f096675a10a240ec6862e6cbd59d32cf8b1fdc1ac04fb7137093690cd97db705e324f6d030344d1d72384504f3465cffccb855c2e29be678'
#   '1da101e67ac09eebbb0682d465075a3657c614426c70907d36fd56fee27df082df6536ac47273f41cd7e145e9ab536a3887a9b118cd8b05887a384070294ceca'
#   'bf5daa4a33daae716a1d7743470dae618151e14ab7bb5d99138f880a908fac57dbb517b78d92c81ecf4532c25366cd32f7acc0e33a711ccde830fbc208726e69'
#   '8a4d1f57c3223c817f840ee989532a57760ad4f836950d18149f4827746f3e7cfb2a1ebdbb115be7c049b5971802eaed9e99125b39cac26b5186b18f9693da99'
#   'ffc8ea3c7875b195720ad238742a726b4b7be0bb8f2f8927358d259202f22b5e32f9ad23a4c66da85e25f36544770c29725be6d99256b685427b94d814e29196'
#   'c2d29d2adbff690099e537d294d08f9ade73f7a744038382f011b4c9f93c29e27629b740dae02361a4e663730459db6fa81bc2903595fe52e71407dab6590ca2'
#   '9dd03f808af45752a01ccbcfec3f3cb39f1a720088e21aa8a19c2ceec3876b3a8b950c1c154203d0adc208fed8ae07a26c8cd59d783e32eb1294a3a340bedad4'
#   '91b2a13fdd2c20c5950ec42c742e8be8ee2b6137a9e73e20cf269415fcc960e90049ab3ca6ec8ddc045a8fa03b16396849494b86ebb742adabb53e2703f2d290'
#   'cd8578ae69d58d4818b0aecca95fa5080586dfaa9bc5050a7203b0f48e50ad64c5b7c1f71e71711ed120223eb2662e96f577855f729bdf10d2cd648a9e305bfe'
#   '4f206967e3d8d1066f5bcb64c35a72bc5f6d69d484b2ab52fd239f4b92b398cdd08c9a016c5dc07fc5cbfdb05983969830983531fae70f67a6a5f61624336577'
#   '61e262c714f0e2f9e2a595f16f203c41df93fbfd3aaf20c3ccdbc2bc6c0285a6591b21346f5f15b23f624e1f72470d5d6e1e805979858ea391c815bc1d2e7c67'
#   'af13f78ff240c00d9e61bd470ace03bc6926e1cf946016c8c4fa27706ed278babc0ec8a04c79b930d9047f62bd7cfcfeba3e7fd493da7476a318fc49ff0e54fe'
#   '5e4fed3c54785fc0140a1cfe970c6ed6a61c0041961999a9777dfcb0050d45e2b9231b3e5e97e025cefe1461614b599bc7129eea931d1996f4849cd83f546abc'
# )
if [[ "${_ns}" == "themartiancompany" ]]; then
  validpgpkeys=(
    # Truocolo
    #   <truocolo@aol.com>
    '97E989E6CF1D2C7F7A41FF9F95684DBE23D6A3E9'
    'DD6732B02E6C88E9E27E2E0D5FC6652B9D9A6C01'
    # Pellegrino Prevete (dvorak)
    #   <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
    '12D8E3D7888F741E89F86EE0FEC8567A644F1D16'
  )
elif [[ "${_ns}" == "freepg" ]]; then
  validpgpkeys=(
    # Andre Heinecke (Release Signing Key)
    '5B80C5754298F0CB55D8ED6ABCEF7E294B092E28'
    # Werner Koch (dist signing 2020)
    '6DAA6E64A76D2840571B4902528897B826403ADA'
    # Niibe Yutaka (GnuPG Release Key)
    'AC8E115BF73E2D8D47FA9908E98E9B2D19C6C8BD'
    # GnuPG.com (Release Signing Key 2021)
    '02F38DFF731FF97CB039A1DA549E695E905BA208'
  )
fi

_git_unbundle() {
  local \
    _tarname="${1}" \
    _bundle \
    _repo \
    _msg=()
  _bundle="${srcdir}/${_tarname}.bundle"
  _repo="${srcdir}/${_tarname}"
  _msg=(
    "Cloning '${_bundle}' into '${_repo}'."
  )
  msg \
    "${_msg[*]}"
  git \
    clone \
      "${_bundle}" \
      "${_repo}" || \
  git \
    -C \
      "${_repo}" \
      pull || \
  true
}

_android_fix() {
  local \
    _bash_files=() \
    _bin_files=() \
    _usr_bin_files=() \
    _makefiles \
    _shell
  _shell="$(
    command \
      -v \
      "bash")"
  mapfile \
    -d \
      $'\0' \
    _bin_files < \
    <(grep \
        -rl \
        '#!/bin' \
        "." |
        tr \
          '\n' \
          '\0' || \
      true)
  mapfile \
    -d \
      $'\0' \
    -O \
      "${#_bin_files[@]}" \
    _bin_files < \
    <(grep \
        -rl \
        '#! /bin' \
        "." |
        tr \
          '\n' \
          '\0' || \
      true)
  mapfile \
    -d \
    $'\0' \
    _usr_bin_files < \
    <(grep \
        -rl \
        '#!/usr/bin' \
        "." |
        tr \
          '\n' \
          '\0' || \
      true)
  _bash_files+=(
    "${_bin_files[@]}"
    "${_usr_bin_files[@]}"
  )
  for _file in "${_bash_files[@]}"; do \
    _msg=(
      "Fixing shebang for"
      "'${_file}'."
    )
    echo \
      "${_msg[*]}"
    termux-fix-shebang \
      "${_file}"
  done
  mapfile \
    -d \
    $'\0' \
    _makefiles < \
    <(grep \
        -rl \
        -e \
          "SHELL = /bin/sh" \
        "." |
        tr \
          '\n' \
          '\0' || \
      true)
  for _file in "${_makefiles[@]}"; do \
    _msg=(
      "Fixing makefile"
      "'${_file}'."
    )
    echo \
      "${_msg[*]}"
    if [[ -e "${_file}" ]]; then
      sed \
        -e \
          "s%SHELL = /bin/sh%SHELL = ${_shell}%g" \
        -i \
        "${_file}"
    else
      _msg=(
        "Somehow '${_file}' seems"
        "not existing despite it"
        "is the result of a grep."
      )
      echo \
        "${_msg[*]}" \
        1>&2
      exit \
        1
    fi
  done
}

prepare() {
  local \
    _bash_files=() \
    _file \
    _os \
    _src
  if [[ "${_evmfs}" == "true" ]]; then
    if [[ "${_git}" == "false" ]]; then
      ur \
        "${_like}"
    elif [[ "${_git}" == "true" ]]; then
      _git_unbundle \
        "${_tarname}"
    fi
  fi
  _os="$(
    uname \
      -o)"
  if [[ "${_archive_format}" == "git" ]]; then
    mv \
      "${srcdir}/${_tarfile}" \
      "${srcdir}/${_tarname}"
  else
    echo \
      "Archive format: '${_archive_format}'"
  fi
  ls \
    "${srcdir}"
  cd \
    "${srcdir}/${_tarname}"
  for _src in "${source[@]}"; do
    _src="${_src%%::*}"
    _src="${_src##*/}"
    [[ "${src}" = *".patch" ]] ||
    continue
    printf \
      "Applying patch %s...\n" \
      "${_src}"
    patch \
      -Np1 < \
      "../${_src}"
  done
  sed \
    -n \
      '5, 28 p' \
    "COPYING.other" > \
    "MIT.txt"
  sed \
    -n \
      '30, 60 p' \
    "COPYING.other" > \
    "BSD-4-Clause.txt"
  sed \
    -n \
      '62, 92 p' \
    "COPYING.other" > \
    "BSD-3-Clause.txt"
  sed \
    -n \
      '95, 125 p' \
    "COPYING.other" > \
    "BSD-2-Clause.txt"
  sed \
    -n \
      '128, 160 p' \
    "COPYING.other" > \
    "Unicode-TOU.txt"
  if [[ "${_os}" == "Android" ]]; then
    _android_fix
  fi
  "./autogen.sh"
}

build() {
  local \
    _configure_opts=() \
    _os \
    _shell
  _os="$(
    uname \
      -o)"
  if [[ "${_os}" == "Android" ]]; then
    _shell="$(
      command \
        -v \
        "bash")"
    echo \
      "Android shell: '${_shell}'."
    # Fix caused by the issue described at
    # https://github.com/termux/termux-packages/29379
    export \
      SHELL="${_shell}"
  fi
  _configure_opts=(
    --enable-g13
    --enable-large-secmem  # prerequisite for large RSA keys
    --enable-maintainer-mode
    --libexecdir="/usr/lib/gnupg"
    --prefix="/usr"
    --sbindir="/usr/bin"
    --sysconfdir="/etc"
  )
  if [[ "${_docs}" == "false" ]]; then
    _configure_opts+=(
      --disable-doc
    )
  fi
  cd \
    "${_tarname}"
  "./configure" \
    "${_configure_opts[@]}"
  make
}

check() {
  cd \
    "${_tarname}"
  make \
    check
}

package() {
  local \
    _make_opts=() \
    _systemdir \
    _unit \
    _wantsdir
  _systemdir="${pkgdir}/usr/lib/systemd"
  _wantsdir="${_systemdir}/user/sockets.target.wants"
  _make_opts+=(
    DESTDIR="${pkgdir}"
  )
  depends+=(
    "bzip2"
    "libbz2.so"
    "libassuan>=${_libassuan_pkgver}"
    "libassuan.so"
    "npth"
    "libnpth.so"
    "readline"
    "libreadline.so"
  )
  cd \
    "${_tarname}"
  make \
    "${_make_opts[@]}" \
    install
  ln \
    -s \
    "gpg" \
    "${pkgdir}/usr/bin/gpg2"
  ln \
    -s \
    "gpgv" \
    "${pkgdir}/usr/bin/gpgv2"
  install \
    -vDm644 \
    "../keyboxd.8" \
    -t \
    "${pkgdir}/usr/share/man/man8/"
  install \
    -vDm644 \
    {"BSD-"{"2","3","4"}"-Clause","MIT","Unicode-TOU"}.txt \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}/"
  install \
    -vdm755 \
    "${_wantsdir}"
  for _unit in "../"*"."{"service","socket"}; do
    case $_unit in
      *@.*)
        install \
          -vDm644 \
          "${_unit}" \
          -t \
          "${_systemdir}/system/" ;;
      *.socket)
        ln \
          -sv \
          "../${_unit##*/}" \
          -t \
          "${_wantsdir}/" ;&
      *)
        install \
          -vDm644 \
          "${_unit}" \
          -t \
          "${_systemdir}/user/" ;;
    esac
  done
}

# vim: ts=2 sw=2 et:
