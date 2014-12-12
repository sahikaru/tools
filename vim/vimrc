set rtp+=~/.vim/bundle/vundle/
call vundle#rc()
Bundle 'gmarik/vundle'
Bundle 'majutsushi/tagbar'
Bundle 'dimasg/vim-mark'
Bundle 'The-NERD-tree'
Bundle 'The-NERD-Commenter'
Bundle 'a.vim'
Bundle 'mattn/emmet-vim'
Bundle 'minibufexpl.vim'
"Bundle 'Lokaltog/powerline', {'rtp': 'powerline/bindings/vim/'}
Bundle "davidhalter/jedi-vim"
Bundle 'tpope/vim-fugitive'
Bundle 'ervandew/supertab'
Bundle 'scrooloose/syntastic'
Bundle 'scrooloose/nerdcommenter'
"Bundle 'chazy/cscope_maps'
"Bundle 'vim-scripts/c-standard-functions-highlight'
Bundle 'kien/ctrlp.vim'
"Bundle 'vim-jp/cpp-vim'
Bundle 'altercation/vim-colors-solarized'
Bundle 'fs111/pydoc.vim'
Bundle 'godlygeek/tabular'
Bundle 'fsouza/go.vim'
"Bundle 'klen/python-mode'

"solarized theme
syntax on

"general setting
set fileencodings=ucs-bom,utf-8,cp936,latin-1,gbk,gb18030
set encoding=utf-8
set helplang=cn
set clipboard=unnamed
set shiftwidth=2
set tabstop=2
set expandtab
set nobackup
set noswapfile
set nowb
set backspace=start,indent,eol
set nu!
set autoindent
set smartindent
set wrap
set nocompatible
filetype off
set hlsearch
set incsearch
filetype plugin indent on
set noerrorbells
set novisualbell
filetype plugin on
filetype indent on
syntax on
set ruler

vmap <C-c> "+y
set mouse=
"autocmd VimEnter * NERDTree
autocmd BufEnter * silent! lcd %:p:h

let Tlist_Show_One_File = 1
let g:miniBufExplMapWindowNavVim = 1 
let g:miniBufExplMapWindowNavArrows = 1 
let g:miniBufExplMapCTabSwitchBufs = 1 
let g:miniBufExplModSelTarget = 1

"akirayu101 modify personal
map <C-N> :bn<cr>
function! LoadCscope()
    let db = findfile("cscope.out", ".;")
    if (!empty(db))
        let path = strpart(db, 0, match(db, "/cscope.out$"))
        set nocscopeverbose " suppress 'duplicate connection' error
        exe "cs add " . db . " " . path
        set cscopeverbose
    endif
endfunction
au BufEnter /* call LoadCscope()


"youcompleteme config
nnoremap <C-]> :YcmCompleter GoToDefinitionElseDeclaration<CR>
let g:ycm_global_ycm_extra_conf = '~/.ycm_extra_conf.py'
let g:ycm_confirm_extra_conf = 0
set completeopt+=preview

"personal abbr
function! ToggleNERDTree()
    let w:jumpbacktohere = 1

    " Detect which plugins are open
    if exists('t:NERDTreeBufName')
        let nerdtree_open = bufwinnr(t:NERDTreeBufName) != -1
    else
        let nerdtree_open = 0
    endif

    " Perform the appropriate action
    if nerdtree_open
        NERDTreeClose
    else
        NERDTree
    endif

    " Jump back to the original window
    for window in range(1, winnr('$'))
        execute window . 'wincmd w'
        if exists('w:jumpbacktohere')
            unlet w:jumpbacktohere
            break
        endif
    endfor
endfunction
nnoremap <leader>\  :call ToggleNERDTree()<CR>
abbr Wqa wqa
abbr Qa qa
abbr tty inferior-tty
nnoremap <leader>t :TagbarToggle<CR>
" Window resizing mappings /*{{{*/
nnoremap <S-Up> :normal <c-r>=Resize('+')<CR><CR>
nnoremap <S-Down> :normal <c-r>=Resize('-')<CR><CR>
nnoremap <S-Left> :normal <c-r>=Resize('<')<CR><CR>
nnoremap <S-Right> :normal <c-r>=Resize('>')<CR><CR>
function! Resize(dir)
    let this = winnr()
    if '+' == a:dir || '-' == a:dir
        execute "normal \<c-w>k"
        let up = winnr()
        if up != this
            execute "normal \<c-w>j"
            let x = 'bottom'
        else
            let x = 'top'
        endif
    elseif '>' == a:dir || '<' == a:dir
        execute "normal \<c-w>h"
        let left = winnr()
        if left != this
            execute "normal \<c-w>l"
            let x = 'right'
        else
            let x = 'left'
        endif
    endif
    if ('+' == a:dir && 'bottom' == x) || ('-' == a:dir && 'top' == x)
        return "5\<c-v>\<c-w>+"
    elseif ('-' == a:dir && 'bottom' == x) || ('+' == a:dir && 'top' == x)
        return "5\<c-v>\<c-w>-"
    elseif ('<' == a:dir && 'left' == x) || ('>' == a:dir && 'right' == x)
        return "5\<c-v>\<c-w><"
    elseif ('>' == a:dir && 'left' == x) || ('<' == a:dir && 'right' == x)
        return "5\<c-v>\<c-w>>"
    else
        echo "oops. check your ~/.vimrc"
        return ""
    endif
endfunction
" /*}}}*/ 
set autoindent                " auto/smart indentation
set cindent
set preserveindent
set copyindent
set smarttab                  " tab and backspace are smart
set tabstop=4                 " 4 spaces
set softtabstop=4

set shiftwidth=4
set expandtab

"clang complete
"let g:clang_complete_copen=1
"let g:clang_periodic_quickfix=1
"let g:clang_snippets=1
"let g:clang_close_preview=1
"let g:clang_use_library=1
"let g:clang_library_path='/usr/lib/libclang.dylib'

"tabular config 
nnoremap <leader>l:Tabularize /=<CR>


let g:tagbar_type_go = {
            \ 'ctagstype' : 'go',
            \ 'kinds'     : [
            \ 'p:package',
            \ 'i:imports:1',
            \ 'c:constants',
            \ 'v:variables',
            \ 't:types',
            \ 'n:interfaces',
            \ 'w:fields',
            \ 'e:embedded',
            \ 'm:methods',
            \ 'r:constructor',
            \ 'f:functions'
            \ ],
            \ 'sro' : '.',
            \ 'kind2scope' : {
            \ 't' : 'ctype',
            \ 'n' : 'ntype'
            \ },
            \ 'scope2kind' : {
            \ 'ctype' : 't',
            \ 'ntype' : 'n'
            \ },
            \ 'ctagsbin'  : 'gotags',
            \ 'ctagsargs' : '-sort -silent'
            \ }
